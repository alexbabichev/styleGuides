# TypeScript Style Guide

*A mostly reasonable approach to TypeScript*


## Table of Contents

1. [Formatting](#formatting)
2. [Line length](#line-length)
3. [Quotes](#quotes)
4. [Spaces](#spaces)
5. [Semicolons](#semicolons)
6. [Todo and XXX](#todo-and-xxx)
7. [Inline Comments](#inline-comments)
8. [Import](#import)
9. [Names](#names)
10. [Types](#types)
11. [Filename](#filename)

## Formatting

The TypeScript compiler ships with a very nice formatting language service. Whatever output it gives by default is good enough to reduce the cognitive overload on the team.

For example use `tsfmt` to automatically format your code on the command line. Also your IDE (*atom / vscode / vs / sublime*) already has formatting support built-in.

Examples:

```js
// Space before type i.e. foo:<space>string
const foo: string = 'hello';
```

Only surround arrow function parameters when necessary.

```js

// Bad
(x) => x + x

// Good
x => x + x
```

## Line Length

Lines must not be longer than 140 characters.

When a statement runs over 140 characters on a line, it should be broken up, ideally after a comma or operator.

## Quotes

Prefer single quotes ( \' ) unless escaping.

> Reason: More JavaScript teams do this (e.g. airbnb, standard, npm, node, google/angular, facebook/react). Its easier to type (no shift needed on most keyboards).

> Double quotes are not without merit: Allows easier copy paste of objects into JSON. Allows people to use other languages to work without changing their quote character. Allows you to use apostrophes e.g.

When you can't use double quotes, try using back ticks ( \` ).

> Reason: These generally represent the intent of complex enough strings.

## Spaces

Use 2 spaces. Not tabs.

> Reason: More JavaScript teams do this (e.g. airbnb, idiomatic, standard, npm, node, google/angular, facebook/react). The TypeScript/VSCode teams use 4 spaces but are definitely the exception in the ecosystem.


## Semicolons

Use semicolons.

> Reasons: Explicit semicolons helps language formatting tools give consistent results. Missing ASI (automatic semicolon insertion) can trip new devs e.g. foo() \\n (function(){}) will be a single statement (not two).

## Todo and XXX

`TODO` and `XXX` annotations help you quickly find things that need to be fixed/implemented.

Use `// TODO:` to annotate solutions that need to be implemented.

Use `// XXX:` to annotate problems the need to be fixed.

It is best to write code that doesn't need `TODO` and `XXX` annotations, but sometimes it is unavoidable.

## Import

Use whitespaces

```js
//Bad
import {BrowserModule} from '@angular/platform-browser';
import {BrowserModule,Component ,OnInit} from '@angular/platform-browser';

// Good
import { BrowserModule } from '@angular/platform-browser';
import { NgModule, Component, OnInit } from '@angular/core';
```

## Names

* Use PascalCase for type names.
* Do not use "I" as a prefix for interface names.
* Use PascalCase for enum values.
* Use camelCase for function names.
* Use camelCase for property names and local variables.
* Do not use "\_" as a prefix for private properties.
* Use whole words in names when possible.

## Types

* Always favor type inference over explicit type declaration except for function return types
* Always define the return type of functions.
* Use the `any` type sparingly, it is always better to define an interface.
* Types should be used whenever necessary (no implicit `any`).
* When possible, allow the compiler to infer type of variables.

```js
// Bad
const output = identify<string>("myString");

// Good
const output = identity("myString");
```

#### Generics

* Use `T` for the type variable if only one is needed.
* If more than one type variable is required, start with letter "T" and name your variable in alphabetical sequence.

```js
function find<T, U extends Findable>(needle: T, haystack: U): U {
  return haystack.find(needle)
}
```

#### Array

Annotate arrays as `foos:Foo[]` instead of `foos:Array<Foo>`.

> Reasons: Its easier to read. Its used by the TypeScript team. Makes easier to know something is an array as the mind is trained to detect [].


## Filename

Name files with camelCase. E.g. `accordian.tsx`, `myControl.tsx`, `utils.ts`, `map.ts` etc.

> Reasons: Its easier to read. Its used by the TypeScript team. Makes easier to know something is an array as the mind is trained to detect [].
