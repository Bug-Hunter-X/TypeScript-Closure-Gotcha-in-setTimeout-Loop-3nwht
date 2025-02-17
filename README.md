# TypeScript Closure Gotcha in setTimeout Loop

This example demonstrates a common issue with closures in JavaScript when used within loops and asynchronous functions like `setTimeout`.  In TypeScript, this issue manifests the same way.

## The Problem

The `printNumbers2` function intends to print numbers 1 through 5 with a slight delay. However, due to the asynchronous nature of `setTimeout` and the closure created around the loop variable `i`, all callbacks will log the final value of `i` (which is 6 after the loop completes) instead of the value of `i` at the time the `setTimeout` was called.

## Solution

To fix this, use an immediately invoked function expression (IIFE) to create a new scope for each iteration of the loop, capturing the current value of `i`. This ensures that each callback has its own copy of `i`.