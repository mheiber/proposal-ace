- [ ] what do we do re `type`/`interface`? Save it for a separate proposal?
- [ ] is it possible to even specify this syntax while keeping the goal of being compatible with TS/Flow/whatever? How do we know when the `Annotation` ends?


# Automatic Colon Elimination

## Status
Current Stage:
* Stage 0

## Authors
* Max Heiber ([github](https://github.com/mheiber), [twitter](https://twitter.com/maxheiber))
* Scott Whittaker ([github](https://github.com/scottrobertwhittaker))

## Motivation
This proposal introduces a new form of comment to JS: comments that are *colocated* with other syntax in an ergonomic matter. The proposal is neutral as to how these comments are used, but their natural use case is to *describe* other parts of syntax.

For example, compare this JS:

```js

function retrieveUser(id) {
    ....
}
```

What is `id`? What is a `User`?

JSDoc and similar tools ride on top of existing syntax to provide awkward, yet sometimes-useful annotations:

```js
/**
 * @param id {String} user Id
 * @return {Object} user
 **/
function retrieveUser(id) {
    ....
}
```

The JSDoc conveys *some* more information at the cost of four LOCs and some redundant information.

Better:

```ts
function retrieveUser(id: string): User {
    ....
}
```

Annotations in TS are useful for code readability and tooling support. However, using existing comment syntax (`/* ... */` and `//`) is unergonomic and wastes space. Overuse of JSDoc comments, for example, can *impair* readability through waste of space.

# Overview
This proposal adds a new form of inline comment to JS.

Any Identifier or PrivateIdentifier may be followed by an Annotation, where an annotation consists of a colon (`:`), followed by `____`.

__TBD__: more precise description. I don't actually know how to do this. How do we know where the annotation ends?

## Notes

## Prior Art

- [TypeScript][ts] is a superset of JavaScript that provides static type checking. [TypeScript has a fully-documented grammar][ts-grammar], using colons to introduce type annotations and angle brackets to introduce type variables in generics.

- The [Flow type checker][flow] provides static type checking for JavaScript files.  Unlike TypeScript, Flow [does not have a specified grammar][flow-no-grammar].  It uses a [similar syntax for generics as TypeScript][flow-generics], but additionally provides syntax for [maybe types][flow-maybe-types] and [exact object types][flow-exact-object-types] which are not grammatical JavaScript.

- [Python][python] provides a [syntax for function annotations, defined in PEP 3107][pep-3107], which are parsed but do not affect the semantics of the program.

[ts]: https://www.typescriptlang.org/index.html
[ts-grammar]: https://github.com/microsoft/TypeScript/blob/master/doc/spec.md#a1-types
[flow]: https://flow.org/
[flow-no-grammar]: https://github.com/facebook/flow/issues/3429
[flow-generics]: https://flow.org/en/docs/types/generics/
[flow-maybe-types]: https://flow.org/en/docs/types/maybe/
[flow-exact-object-types]: https://flow.org/en/docs/lang/width-subtyping/
[python]: https://www.python.org/
[pep-3107]: https://www.python.org/dev/peps/pep-3107/

### Different approaches

- [Google Closure Compiler][closure] is a JavaScript-to-JavaScript optimizing compiler which supports type annotations. Its ["types always appear in comments, never in the syntax of JavaScript itself."][closure-types]

- The [JSDoc documentation system][jsdoc] annotates types using a [comment-based syntax][jsdoc-types] which extends the Closure Compiler's syntax.

- The [Sorbet library for Ruby][sorbet] annotates types using a [decorator-like syntax][sorbet-types] implemented using metaprogramming.

[closure]: https://github.com/google/closure-compiler/
[closure-types]: https://github.com/google/closure-compiler/wiki/Types-in-the-Closure-Type-System
[jsdoc]: https://jsdoc.app/
[jsdoc-types]: https://jsdoc.app/tags-type.html
[sorbet]: https://sorbet.org/
[sorbet-types]: https://sorbet.org/docs/sigs

## Specification
- TBD

## TODO
Per the [TC39 process document](https://tc39.github.io/process-document/), here is a high level list of work that needs to happen across the various proposal stages.

* [ ] Identify champion to advance addition (stage-1)
* [ ] Prose outlining the problem or need and general shape of the solution (stage-1)
* [ ] Illustrative examples of usage (stage-1)
* [ ] High-level API (stage-1)
* [ ] Initial spec text (stage-2)
* [ ] Finalize and reviewer signoff for spec text (stage-3)
* [ ] Test262 acceptance tests (stage-4)
* [ ] tc39/ecma262 pull request with integrated spec text (stage-4)
* [ ] Reviewer signoff (stage-4)
* [ ] Two complete implementations (stage-4)

## References
- TBD

## Prior discussion
- TBD
