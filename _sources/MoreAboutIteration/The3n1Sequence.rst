..  Copyright (C)  Brad Miller, David Ranum, Jeffrey Elkner, Peter Wentworth, Allen B. Downey, Chris
    Meyers, and Dario Mitchell. Permission is granted to copy, distribute
    and/or modify this document under the terms of the GNU Free Documentation
    License, Version 1.3 or any later version published by the Free Software
    Foundation; with Invariant Sections being Forward, Prefaces, and
    Contributor List, no Front-Cover Texts, and no Back-Cover Texts. A copy of
    the license is included in the section entitled "GNU Free Documentation
    License".

.. qnum::
   :prefix: iter-5-
   :start: 1

The 3n + 1 Sequence
-------------------

As another example of indefinite iteration, let's look at a sequence of integers that mathematicians find interesting. The rule for creating the sequence is to start from some given number, call it ``n``. The next term of the sequence is:

- ``n / 2``, if ``n`` is even
- ``3n + 1``, if ``n`` is odd

The sequence stops when ``n`` becomes 1.

This Python function captures that algorithm. Try running this program several times supplying different values for n.

.. activecode:: ch07_indef1

    def sequence_3n_plus_one(n):
        """ Print the 3n+1 sequence from n, terminating when it reaches 1."""

        while n != 1:

            print(n)

            if n % 2 == 0:
                n = n // 2
            else:
                n = 3*n + 1

        print(n)

    sequence_3n_plus_one(3)


The condition for this ``while`` loop is ``n != 1``.  In other words, the loop will continue running until ``n == 1``, since this is precisely when the condition `n != 1` evaluates to ``False``.

Each time through the loop, the program prints the value of ``n`` and then checks whether it is even or odd using the remainder operator. If it is even, the value of ``n`` is divided by 2 using integer division. If it is odd, the value is replaced by ``3*n + 1``.

Try

Since ``n`` sometimes increases and sometimes decreases, it is not clear that ``n`` will ever reach 1, or that the program terminates. For some particular values of ``n``, we can prove that the sequence eventually reaches 1. For example, if the starting value is a power of two, then the value of ``n`` will be even each time through the loop until it reaches 1.

You might like to have some fun and see if you can find a small starting number that needs more than a hundred steps before it terminates.

Particular values aside, the interesting question is whether we can prove that this sequence terminates for *all* values of ``n``. So far, no one has been able to prove it *or* disprove it!

Think about what would be needed for to prove or disprove the hypothesis *All positive integers will eventually converge to 1*.  With fast computers, we have been able to test every integer up to very large values, and so far, they all eventually end up at 1. But this doesn't mean that there might not be some as-yet untested number which does not reduce to 1.

You'll notice that if you don't stop when you reach one, the sequence gets into its own loop: 1, 4, 2, 1, 4, 2, 1, 4, and so on. One possibility is that there might be other cycles that we just haven't found.

Choosing Between for and while
===============================

Use a ``for`` loop if you know the maximum number of times that you'll need to execute the body. For example, if you're traversing a list of elements, or can formulate a suitable call to ``range``, then choose the ``for`` loop.

Any problem statement like "search this list of words" or "check all integers up to 10000 to see which are prime" suggest that a ``for`` loop is best.

By contrast, if you are required to repeat some computation until some condition is met, as we did in this 3n + 1 problem, you'll need a ``while`` loop.

As we noted before, the first case is called a **definite iteration**--we have definite bounds for what is needed. The latter case is called an **indefinite iteration**--we are not sure how many iterations we'll need. For an indefinite iteration, it is generally impossible to determine the maximum number of times the loop might run!
