:orphan:

.. activecode:: xunit.h
   :language: cpp

   #ifndef MINUNIT_MINUNIT_H
   #define MINUNIT_MINUNIT_H

   #ifdef __cplusplus
      extern "C" {
   #endif

   #if !defined(_POSIX_C_SOURCE) || _POSIX_C_SOURCE < 200112L
   #undef _POSIX_C_SOURCE
   #define _POSIX_C_SOURCE 200112L
   #endif

   #include <unistd.h>
   #include <time.h>
   #include <sys/time.h>
   #include <sys/resource.h>
   #include <sys/times.h>
   #include <string.h>

   #if __GNUC__ >= 5 && !defined(__STDC_VERSION__)
   #define __func__ __extension__ __FUNCTION__
   #endif

   #else
   #error "Unable to define timers for an unknown OS."
   #endif

   #include <stdio.h>
   #include <math.h>

   //  Maximum length of last message
   #define MINUNIT_MESSAGE_LEN 1024
   //  Accuracy with which floats are compared
   #define MINUNIT_EPSILON 1E-12

   //  Misc. counters
   static int minunit_run = 0;
   static int minunit_assert = 0;
   static int minunit_fail = 0;
   static int minunit_status = 0;

   //  Timers
   static double minunit_real_timer = 0;
   static double minunit_proc_timer = 0;

   //  Last message
   static char minunit_last_message[MINUNIT_MESSAGE_LEN];

   //  Test setup and teardown function pointers
   static void (*minunit_setup)(void) = 0;
   static void (*minunit_teardown)(void) = 0;

   #define MU_TEST(method_name) static void method_name(void)
   #define MU_TEST_SUITE(suite_name) static void suite_name(void)

   #define MU__SAFE_BLOCK(block) do {\
      block\
   } while(0)

   //  Run test suite and unset setup and teardown functions
   #define MU_RUN_SUITE(suite_name) MU__SAFE_BLOCK(\
      suite_name();\
      minunit_setup = NULL;\
      minunit_teardown = NULL;\
   )

   //  Configure setup and teardown functions
   #define MU_SUITE_CONFIGURE(setup_fun, teardown_fun) MU__SAFE_BLOCK(\
      minunit_setup = setup_fun;\
      minunit_teardown = teardown_fun;\
   )

   //  Test runner
   #define MU_RUN_TEST(test) MU__SAFE_BLOCK(\
      if (minunit_real_timer==0 && minunit_proc_timer==0) {\
         minunit_real_timer = mu_timer_real();\
         minunit_proc_timer = mu_timer_cpu();\
      }\
      if (minunit_setup) (*minunit_setup)();\
      minunit_status = 0;\
      test();\
      minunit_run++;\
      if (minunit_status) {\
         minunit_fail++;\
         printf("F");\
         printf("\n%s\n", minunit_last_message);\
      }\
      fflush(stdout);\
      if (minunit_teardown) (*minunit_teardown)();\
   )

   //  Report
   #define MU_REPORT() MU__SAFE_BLOCK(\
      double minunit_end_real_timer;\
      double minunit_end_proc_timer;\
      printf("\n\n%d tests, %d assertions, %d failures\n", minunit_run, minunit_assert, minunit_fail);\
      minunit_end_real_timer = mu_timer_real();\
      minunit_end_proc_timer = mu_timer_cpu();\
      printf("\nFinished in %.8f seconds (real) %.8f seconds (proc)\n\n",\
         minunit_end_real_timer - minunit_real_timer,\
         minunit_end_proc_timer - minunit_proc_timer);\
   )
   #define MU_EXIT_CODE minunit_fail

   //  Assertions
   #define mu_check(test) MU__SAFE_BLOCK(\
      minunit_assert++;\
      if (!(test)) {\
         snprintf(minunit_last_message, MINUNIT_MESSAGE_LEN, "%s failed:\n\t%s:%d: %s", __func__, __FILE__, __LINE__, #test);\
         minunit_status = 1;\
         return;\
      } else {\
         printf(".");\
      }\
   )

   #define mu_fail(message) MU__SAFE_BLOCK(\
      minunit_assert++;\
      snprintf(minunit_last_message, MINUNIT_MESSAGE_LEN, "%s failed:\n\t%s:%d: %s", __func__, __FILE__, __LINE__, message);\
      minunit_status = 1;\
      return;\
   )

   #define mu_assert(test, message) MU__SAFE_BLOCK(\
      minunit_assert++;\
      if (!(test)) {\
         snprintf(minunit_last_message, MINUNIT_MESSAGE_LEN, "%s failed:\n\t%s:%d: %s", __func__, __FILE__, __LINE__, message);\
         minunit_status = 1;\
         return;\
      } else {\
         printf(".");\
      }\
   )

   #define mu_assert_int_eq(expected, result) MU__SAFE_BLOCK(\
      int minunit_tmp_e;\
      int minunit_tmp_r;\
      minunit_assert++;\
      minunit_tmp_e = (expected);\
      minunit_tmp_r = (result);\
      if (minunit_tmp_e != minunit_tmp_r) {\
         snprintf(minunit_last_message, MINUNIT_MESSAGE_LEN, "%s failed:\n\t%s:%d: %d expected but was %d", __func__, __FILE__, __LINE__, minunit_tmp_e, minunit_tmp_r);\
         minunit_status = 1;\
         return;\
      } else {\
         printf(".");\
      }\
   )

   #define mu_assert_double_eq(expected, result) MU__SAFE_BLOCK(\
      double minunit_tmp_e;\
      double minunit_tmp_r;\
      minunit_assert++;\
      minunit_tmp_e = (expected);\
      minunit_tmp_r = (result);\
      if (fabs(minunit_tmp_e-minunit_tmp_r) > MINUNIT_EPSILON) {\
         int minunit_significant_figures = 1 - log10(MINUNIT_EPSILON);\
         snprintf(minunit_last_message, MINUNIT_MESSAGE_LEN, "%s failed:\n\t%s:%d: %.*g expected but was %.*g", __func__, __FILE__, __LINE__, minunit_significant_figures, minunit_tmp_e, minunit_significant_figures, minunit_tmp_r);\
         minunit_status = 1;\
         return;\
      } else {\
         printf(".");\
      }\
   )

   #define mu_assert_string_eq(expected, result) MU__SAFE_BLOCK(\
      const char* minunit_tmp_e = expected;\
      const char* minunit_tmp_r = result;\
      minunit_assert++;\
      if (!minunit_tmp_e) {\
         minunit_tmp_e = "<null pointer>";\
      }\
      if (!minunit_tmp_r) {\
         minunit_tmp_r = "<null pointer>";\
      }\
      if(strcmp(minunit_tmp_e, minunit_tmp_r)) {\
         snprintf(minunit_last_message, MINUNIT_MESSAGE_LEN, "%s failed:\n\t%s:%d: '%s' expected but was '%s'", __func__, __FILE__, __LINE__, minunit_tmp_e, minunit_tmp_r);\
         minunit_status = 1;\
         return;\
      } else {\
         printf(".");\
      }\
   )

   static double mu_timer_real(void)
   {
      struct timeval tm;
      {
         struct timespec ts;
         const clockid_t id = CLOCK_MONOTONIC;
         if ( id != (clockid_t)-1 && clock_gettime( id, &ts ) != -1 )
            return (double)ts.tv_sec +
               (double)ts.tv_nsec / 1000000000.0;
      }

      gettimeofday( &tm, NULL );
      return (double)tm.tv_sec + (double)tm.tv_usec / 1000000.0;
   }

   static double mu_timer_cpu(void)
   {
      {
         const double ticks = (double)sysconf( _SC_CLK_TCK );
         struct tms tms;
         if ( times( &tms ) != (clock_t)-1 )
            return (double)tms.tms_utime / ticks;
      }

   }

   #ifdef __cplusplus
   }
   #endif

   #endif /* MINUNIT_MINUNIT_H */



