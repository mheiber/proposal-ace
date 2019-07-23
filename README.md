- [ ] what do we do re `type`/`interface`? Save it for a separate proposal?
- [ ] is it possible to even specify this syntax while keeping the goal of being compatible with TS/Flow/whatever? How do we know when the `Annotation` ends?


# Automatic Colon Elimination

## Status
Current Stage:
* Stage 0

## Authors
* Max Heiber ([github](https://github.com/mheiber), [twitter](https://twitter.com/maxheiber))
* Scott Whittaker __TODO__ links

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
function retriveUser(id) {
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

Any Identifier or PrivateIdentifier may be followed by an Annotation, where an annotation consists of a colon (`:`), followed by ____.

__TBD__: more precise description. I don't actually know how to do this. How do we know where the annotation ends?

## Notes

## Prior Art
- Python __TODO__
- Clojure Compiler __TODO__
- JSDoc __TODO__
- Flow __TODO__
  - comment-based Flow __TODO__
- TypeScript __TODO__
- Sorbet for Rub __TODO__

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
