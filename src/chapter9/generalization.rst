Generalization
--------------

In some ways converting from base 60 to base 10 and back is harder than
just dealing with times. Base conversion is more abstract; our intuition
for dealing with times is better.

But if we have the insight to treat times as base 60 numbers, and make
the investment of writing the conversion functions (``convertToSeconds``
and ``makeTime``), we get a program that is shorter, easier to read and
debug, and more reliable.

It is also easier to add more features later. For example, imagine
subtracting two ``Time``\ s to find the duration between them. The naive
approach would be to implement subtraction with borrowing. Using the
conversion functions would be easier and more likely to be correct.

Ironically, sometimes making a problem harder (more general) makes is
easier (fewer special cases, fewer opportunities for error).

