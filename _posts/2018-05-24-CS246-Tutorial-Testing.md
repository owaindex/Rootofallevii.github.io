---
layout: post
title: CS246 Tutorial: Testing
description: CS246 extra tutorial on testing.
date: 2018-05-24
category:
- CS
- 2018-Spring-2A
---



## CS246 Tutorial: Testing

#### Failure, Error, Default

The *Existence of an observable **failure** implies an internal **error** due to some root **default**.*

- **Fault**: static defect in the software.
- **Error**: an incorrect internal state that is the manifestation of the fault.
- **Failure**: external incorrect behavior with respect to the requirements or other description of the expected behavior.

*A headache* (failure) implies I have *high blood pressure* (error) due to *irregular sleeping patterns* (fault). 



#### Testing vs. Debugging

- **Testing**: detecting failures in your program.
- **Debugging**: locating and fixing the root faults.



#### Black-box Testing

- **Equivalence Partitioning**: pick one representative from each equivalence class to test.
- **Boundary Value Testing**: testing boundary values.

- **Error Guessing**: try inputs are likely to cause failures (e.g. edge cases).
- **Fuzz Testing**: generate a large set of plausible inputs for the program to try and break it.



#### White-box Testing

- Attempt to test every branch of every single function (or even every single path) in the code.
- It may not be possible to actually test all possible execution paths, though tools exist to measure **test coverage** (how much of your code is being run by the tests).



#### Assertions

- **Pre-condition**: test properties of parameters at top of a function.
- **Invariant**: test some property in an intermediate stage of the computation.
- **Post-condition**: test some property before returning from a function.
- **Non-null**: checking that pointers are not null
- **Unreachable**: use `assert(false);` to state that a particular code path will never be executed. 



###### C++ Trick

```C++
int payroll(int hourly_rate, int hours_worked) {
    assert( hourly_rate > 0 && "hourly rate should be positive");
    assert( hours_worked >= 0 && "cannot work negative hours");
    // ... 
}
```

- A string literal is treated as a non-null pointer, which a *true* value in C++. 
- Thus the failure of `assert` indicates the first condition was not met.
- Including a message in assertions allows it to be printed, along with the source file and the line number, to our debugging process easier. 



#### Unit Testing & Integration Testing

- **Unit Testing**: test individual components of a program (e.g. interface of a single function)
- **Integration Testing**: test the interactions between larger parts of the program, up to and including the whole thing.



#### Final Tip

>  Research shows that people tend to test cases that "should work" much more than the tests which "should fail". However, the "should fail" cases can often be more useful at detecting faults. 