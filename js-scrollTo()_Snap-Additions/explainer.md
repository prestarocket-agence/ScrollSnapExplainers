# JS `snapTo()`

### Status of this Document
This document is intended as a starting point for engaging the community and standards bodies in developing collaborative solutions fit for standardization. As the solutions to
problems described in this document progress along the standards-track, we will retain this document as an archive and use this section to keep the community up-to-date with the
most current standards venue and content location of future work and discussions.
* This document status: **Active**
* Expected venue: [W3C](https://www.w3.org)
* Current version: this document

## Introduction

[Scroll snap points](https://www.w3.org/TR/css-scroll-snap-1/) are an important and powerful CSS feature. They enable the creation of pointer agnostic stepped scroll experiences, and do so very succinctly. The problem is, they're often used alongside adjacent elements which need to represent this stepped state of scroll, aka the user needs a way to see the state of the snap. Developers today write Javascript observers or create custom functions to monitor and drive this state. 

Wiring up "snap to next", "snap to last" or "snap to the clicked item" should be trivial methods to call on a snap container.

### Goals

To empower the scroll snapping container with an API for iterating through snap children in a reasonable way, for all snapping containers, including [2-dimensional matrix layouts](https://codepen.io/argyleink/pen/MWWpOmz) and support for all document directions and writing modes.

### Use Cases

1. Carousels
2. Sliders
3. Tabousels or Carotabs
4. Media galleries
5. Slides
6. Click/tap and snap to item

<br>

## Proposed Additions

#### `scrollTo()`
MDN https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollTo

#### `scrollIntoView()`
MDN https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollIntoView

Currently these api's `scrollToOptions` and this proposal ([inspired by Majid](https://github.com/argyleink/ScrollSnapExplainers/discussions/6#discussioncomment-868440)) seeks to add keyword **values** to the side (top, block, left, inline) properties, to control the scroll snap aspects of the scroller specifically. 

Additions:
- `snap-next`
- `snap-prev`
- `snap-first`
- `snap-last`

Example usage:  
```js
// basic
container.scrollTo({
  left: 'snap-next',
})

// control animation
container.scrollTo({
  left: 'snap-next',
  behavior: 'smooth',
})

// 2d case
container.scrollTo({
  left: 'snap-first',
  top: 'snap-first',
  behavior: 'instant',
})

// to a specific element
container.querySelector('.child-2').scrollIntoView({
  top: 'snap',
  behavior: 'smooth',
})
```

<br>

## Privacy and Security Considerations

### Privacy

There are no known privacy impact of this feature.

### Security

There are no known security impacts of this feature.

## Contributing
For now, please use this [Discussion](https://github.com/argyleink/ScrollSnapExplainers/discussions/13) for comments and questions, or a Pull Request to offer changes 🙏