[![build status](https://secure.travis-ci.org/dankogai/swift-pons.png)](http://travis-ci.org/dankogai/swift-pons)

# swift-pons
Protocol-Oriented Number System in Pure Swift

![typetree](./typetree.png)

## SYNOPSIS

````swift
import PONS                     // Let the fun begin!

let bn = BigInt(1)<<64 + 1      // 18446744073709551617
bn.asUInt64                     // nil; bn > UIntMax.max
(bn - 2).asUInt64               // 18446744073709551615 == UIntMax.max
bn + bn // 36893488147419103234
bn - bn // 0
bn * bn // 340282366920938463500268095579187314689
bn / bn // 1

let bq = BigInt(1).over(bn)     // (1/18446744073709551617)
bq + bq // (2/18446744073709551617)
bq - bq // (0/1)
bq * bq // (1/340282366920938463500268095579187314689)
bq / bq // (1/1)
bq.denominator == bn            // true, of course!
bq.reciprocal.numerator == bn   // so is this

let bz = bq + bq.i  // ((1/18446744073709551617)+(1/18446744073709551617).i)
bz + bz // ((2/18446744073709551617)+(2/18446744073709551617).i)
bz - bz // ((0/1)+(0/1).i)
bz * bz // ((0/1)+(2/340282366920938463500268095579187314689).i)
bz / bz // ((1/1)+(0/1).i)
````

## USAGE

### With Playground via Workspace

Build the framework before having fun.

![](screenshots/select-scheme.png)

To do so, all you need is choose Framework-OSX from the scheme and build it.  With framework done, 
get back to the OSX playground and enjoy.

### With Your Project

0. Just copy pons/*.swift to your project
1. Or build framework and copy it to your project

### With REPL

#### OS X

Simply `make repl` in the top directory.

#### Linux

````
make SWIFTPATH=${YOUR_SWIFT_PATH} repl # ${YOUR_SWIFT_PATH}=~/swift/usr/bin in my case
````

## REQUIREMENT

Swift 2.1 or better.  Linux supported.

With Swift 2.2 you get some deprecation warnings like:

````
pons/pocomplex.swift:13:5: warning: use of 'typealias' to declare associated types is deprecated; use 'associatedtype' instead
    typealias RealType:POSignedNumber
    ^~~~~~~~~
```

Just ignore them for the time being.  They are needed in 2.1.
