# Solid Slider

[![size](https://img.shields.io/bundlephobia/minzip/solid-slider?style=for-the-badge)](https://bundlephobia.com/package/solid-slider)
[![size](https://img.shields.io/npm/v/solid-slider?style=for-the-badge)](https://www.npmjs.com/package/solid-slider)
![npm](https://img.shields.io/npm/dw/solid-slider?style=for-the-badge)

A carousel/slider implementation in TypeScript for SolidJS. It's built on KeenSlider 6, an open-source library agnostic touch slider with native touch/swipe behavior and great performance. It comes with no dependencies, TypeScript support, multitouch support and is compatible with all common browsers.

## Installation

```bash
npm install solid-slider --save
yarn add solid-slider ## or in yarn
```

Add as a module:

```ts
import "solid-slider/dist/slider.css";
import createSlider from "solid-slider";
```

## Implementation

Solid Slider is meant to be a lightweight and compact wrapper of KeenSlider. It exposes helpers to make working with the slider convenient. Note that the when the slider mounts it assumes all children in the el are slides. You can override this functionality by passing in a "selector" value to target the specific slides you'd like to include.

Thie library exports it's own CSS which is the basic KeenSlider implementation for convenience. If you supply options as an accessor function, the slider will reactively update the configuration so that you don't have to destroy and recreate the slider. As of KeenSlider 6 plugins are now fully supported. You may supply them as a param in createSlider. Note that plugins are not reactively updated and must be supplied on creation.

## Demo

You can find a functional demo of the slider with most features implemented here: https://codesandbox.io/s/solid-slider-j0x2g

## Example

The following is an example of how to create and then bind options using a directive.

```ts
const MyComponent = () => {
  const options = { duration: 1000 };
  const [slider, { current, next, prev, moveTo }] = createSlider(options);
  return (
    <div use:slider>
      <div>Slide 1</div>
      <div>Slide 2</div>
      <div>Slide 3</div>
    </div>
  );
};
```

or without a directive:

```ts
const MyComponent = () => {
  let ref: HTMLElement;
  const options = { duration: 1000 };
  const [slider, { current, next, prev, moveTo }] = createSlider(options);
  onMount(() => {
    slider(ref);
  });
  return (
    <div ref={ref}>
      <div>Slide 1</div>
      <div>Slide 2</div>
      <div>Slide 3</div>
    </div>
  );
};
```

## Changelog

- 1.0.0 - Initial release
- 1.0.3 - Changed the exported API to be slightly more flexible.
- 1.1.1 - Upgraded to KeenSlider 6 and improved general reactivity.

## Keen Options API

You can set options to the slider via parameters. Note that there are other hooks available as well. Only a subset of useful methods are exposed via the primitive although you can access the slider instance as well from the exports to use the methods directly.

- [Options](https://keen-slider.io/api/#options)
- [Event Hooks](https://keen-slider.io/api/#event-hooks)
- [Methods](https://keen-slider.io/api/#methods)
