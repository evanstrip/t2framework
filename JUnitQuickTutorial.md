# JUnit 4.x Quick Tutorial #

by Wishnu Prasetya

This tutorial is for novice Java programmers who try to learn JUnit.


### How does JUnit work? ###

JUnit is a library packed in a jar file. Among other things it contains a tool (called test runner) to run your test files. It is not an automated testing tool: you still have to write your test files by hand. JUnit does give you some support so that you can write those test files more conveniently.

Suppose you have a class _C_ that you want to test. We will write the tests in a new class; let’s call it _Ctest_. This _Ctest_ is our test file. Actually, test class is a better name. We will typically group the tests in _Ctest_ in a bunch of methods called test methods. You will see an example soon.

To actually test _C_ we need to execute its test class _Ctest_. This is done by calling JUnit’s test runner tool; we pass the name _Ctest_ to it. That’s all. JUnit will then execute _Ctest_ for you.

JUnit will report how many of the test methods in _Ctest_ succeed, and how many fail. The
detail of each failure will be reported; this will be in the form of a print of Java’s stack trace leading to the location of the failure.

### Locate it first ###

If you don’t have JUnit yet, you need to download it (from JUnit site). To use it you just need the jar file. A full download also contains its documentation.

Now locate where this jar file is; it is usually called:

```
junit-<version-number>.jar
```

To use JUnit you will need to add the full path to this jar to your class path. We will see examples latter.


### A simple example ###

Let us consider the simple class below. This is the class that we want to test; but first let me explain a bit about what it is.

The class is called `Subscription`; an instance of it represents a subscription to something (e.g. newspaper, but it doesn’t really matter here). Each subscription has its total price, stored in the variable `price`. This price is in Euro-cent. It also has the length of the subscription, given in months.

```
public class Subscription {

   private int price ; // subscription total price in euro-cent
   private int length ; // length of subscription in months

   // constructor :
   public Subscription(int p, int n) {
     price = p ;
     length = n ;
   }

  /**
   * Calculate the monthly subscription price in euro,
   * rounded up to the nearest cent.
   */
   public double pricePerMonth() {
     double r = (double) price / (double) length ;
      return r ;
   }

  /**
   * Call this to cancel/nulify this subscription.
   */
   public void cancel() { length = 0 ; }

}
```

For example, `new Subscription(1000,2)` will create a new subscription of 1000 Euro-cent for the total period of 2 months.

By the way, the class has a number of bugs; e.g. `pricePerMonth` is supposed to return the price per month in euro. However it calculates the price in cent.

### Let’s write a test ###

Let us write two simple tests to check if pricePerMonth correctly calculates the price per month:

  1. If we have a subscription of 200 cent for a period of 2 month, its monthly price should be 1 euro, right?
  1. The monthly price is supposed to be rounded up to the nearest cent. So, if we have a subscription of 200 cent for a period of 3 month, its monthly price should be exactly 0.67 euro.

Of course we can write tests without JUnit; but this tutorial is about JUnit. So here is how we write them in JUnit.

Each of the tests above will be implemented as a test method; you then group your test methods in a test class. Usually you would group all the test methods that test a certain target class _C_ is a test class called _CTest_, but you can also have multiple test classes if you want, and call them whatever you want.

Here is my test class implementing the above two tests:

```
import org.junit.* ;
import static org.junit.Assert.* ;

public class SubscriptionTest {

   @Test
   public void test_returnEuro() {
      System.out.println("Test if pricePerMonth returns Euro...") ;
      Subscription S = new Subscription(200,2) ;
      assertTrue(S.pricePerMonth() == 1.0) ;
   }

   @Test
   public void test_roundUp() {
      System.out.println("Test if pricePerMonth rounds up correctly...") ;
      Subscription S = new Subscription(200,3) ;
      assertTrue(S.pricePerMonth() == 0.67) ;
   }
}
```

The marker `@Test` is called an annotation in Java. When we later execute JUnit’s test runner it needs to know which methods in your test class are test methods (e.g. you may have several helper methods in your test class). The `@Test` is used to mark that a method is a test method.

In the first test (`test_returnEuro`) we first create a `Subscription`; we call it `S`. Then we want to check that `S.pricePerMonth()` will return the expected value of 1.0. The checking is done by the code:

```
assertTrue(S.pricePerMonth() == 1.0)
```

By the way, the annotation `@Test` and the method `assertTrue` are things exported by the JUnit library; so you need the imports as in the above code to use them.

(Note: some people pointed out that I should not compare a double using
== as I did above, due to possible rounding imprecission. However, in
this case, the value should exact up to two decimals; so using == is
reasonable.)

### Compiling and executing your test ###

Next we want to execute the above test class (`SubscriptionTest`). I’ll show how to do this from a _console_. If you use an IDE the steps are a bit different.

Open a console. You first need to compile the test class, and then you can execute it. The
commands are (in Windows):

```
prompt> javac -cp .;<full path to JUnit.jar> SubscriptionTest.java

prompt> java  -cp .;<full path to JUnit.jar> org.junit.runner.JUnitCore SubscriptionTest
```

(In e.g. Mac you probably have to use ':' instead of ';')


The first command will compile the test class. The second will execute JUnit’s test runner; we pass to it the name of your test class.

This is what you will get from JUnit; it reports that both tests fail. Notice also that it reports which lines exactly in your test class fail.

```
Time: 0,015

There were 2 failures:

   1) test_returnsEuro(SubscriptionTest)
      java.lang.AssertionError:
      ...
      at SubscriptionTest.test_returns_Euro(SubscriptionTest.java:13)
      ...

   2) test_roundUp(SubscriptionTest)
      ...
      at SubscriptionTest.test_roundUp(SubscriptionTest.java:19)
      ...

Tests run: 2, Failures: 2
```

The next thing you want to do is to fix your `Subscription` class and then test it again. We keep fixing it until we get no more failures. You may in the mean time also want to add more tests to your test class.


### What now!? ###

That’s it! Now go and write your own tests.


### Check out my other tutorials ###

  * Wishnu Prasetya, [A tutorial for basic use of Javadoc](JavadocQuickTutorial.md)