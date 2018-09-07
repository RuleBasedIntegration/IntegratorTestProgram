              **D R A F T - Work in progress**

# Integrator Test Program
### A Mathematica program for testing Rubi and Mathematica's built-in integrator

This Mathematica package consists of an integrator test program and a test suite of over 70000 integration problems.
The program can test both Rubi and Mathematica's built-in integrator on all or some of the problems.
It generates a notebook showing the problems on which the integrator being tested is deficient.
These test results can optionally be saved as a notebook file.
Mathematica 7 or later is required to run the test program.

For Mathematica 11.2 or later, use the `PacletInstall` command

```mathematica
PacletInstall[
  "https://github.com/RuleBasedIntegration/IntegratorTestProgram/releases/download/???/IntegratorTestProgram-???.paclet"
]
```
to download the current integrator test program paclet directly from the online repository on GitHub, and
then install it on your computer as a Mathematica package named `IntegratorTestProgram`.

After installing the package, use the `Get` command
```mma
<<IntegratorTestProgram`
```
to load the test program into Mathematica.
This defines the command functions `TestRubi` and `TestMathematica` that test Rubi and Mathematica's built-in integrator, respectively.

If `filenames` is a test file name or list of file names, `TestRubi[filenames]` tests Rubi on the integration problems in the list of files.
For example, the command
```mma
TestRubi[$IndependentTestFiles]
```
tests Rubi on collections of integration problems developed independently by authors of calculus textbooks, implementors of computer algebra systems and others.
Running the test generates a notebook that shows the problems on which Rubi is deficient.
For each deficient result the following is shown:
* The problem number and a brief explanation why the result is deficient
* The problem integral
* The optimal antiderivative, its expression type, leaf size, and the number of steps Rubi uses to integrate it
* The result produced by the integrator being tested, its expression type, leaf size, and the number of steps used to integrate it (if Rubi is being tested)

If `testname` is a string, `TestRubi[filenames,testname]` generates a notebook of deficient test results and saves it as a file with `testname` and Rubi's version number included in its name.
For example, the command
```mma
TestRubi[$IndependentTestFiles, "Independent"]
```
saves the test results as the notebook `Rubi 4.16.0.4 Independent Integration Test Results.nb`.

The arguments and effect of `TestMathematica` commands is the same as for `TestRubi`.
