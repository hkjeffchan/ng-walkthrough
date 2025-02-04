[![npm version](https://badge.fury.io/js/angular-walkthrough.svg)](https://badge.fury.io/js/angular-walkthrough) [![Downloads](https://img.shields.io/npm/dm/angular-walkthrough.svg)](https://www.npmjs.com/package/angular-walkthrough) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/harvest-dev/ng-walkthrough/master/LICENSE.md)

# Walkthrough

This Angular model is inspired in part by [ng-walkthrough](https://github.com/souly1/ng-walkthrough) for AngularJS.

## Installation

```
npm i angular-walkthrough --save
```

## Requirements

-   Angular 11.0.0 and more
-   Angular/cdk 11.0.0 and more

For Angular 6~11 use 0.8.2

## Demo

[See a demo](https://harvest-dev.github.io/ng-walkthrough/dist/ng-walkthrough/).

## Usage

### `ng-walkthrough` attributes

All attributes are optional.

-   `id`: HTML id.

**Output events**

-   `ready`: fired when the walkthrough is completely ready
-   `closed`: fired when the walkthrough has been closed. It sends a boolean value set to true if the walkthrough has been closed with the "finishButton" button.
-   `finished`: fired when the walkthrough has been finished, which means : closed on last step.

**Focus zone**:

-   `focusElementSelector`: CSS selector for focus a HTML element. If the selector detect more that one, the only the first will be chosen.
-   `focusElementCSSClass`: Add a class on focusElement
-   `focusHighlightAnimation`: `true` for show highlight animation on the focus element. By default `false`.
-   `focusBackdrop`: `true` for show a dark backdrop around the focus element. By default `false`.
-   `focusGlow`: `true` for show a glow on the focus element. By default `false`.
-   `focusClick`: add an action `click` on the highlight zone.
-   `typeSelector`: type of selection. Two modes possible: `element` (one unique HMLT element), `zone` (a zone with contains the first and last element). By default : `element`.
-   `radius`: apply a “borderRadius” on highlight zone. If `number` the value as change in percent. If `auto` use the focused element borderRadius. If it's a simple `string`, use it without changes. By default, no radius.
-   `marginZone`: add a maring of focus zone in px. (e.g. `12 15 12 13` for CSS `12px 15px 12px 13px`, `12 15` for `12px 15px 12px 15px`, `12` for `12px 12px 12px 12px`.)
-   `scrollOnTarget`: if the walkthrough detects that `focusElementSelector` is outside of the current view, scrolls automatically. By default : `true`
-   `visibilityCallback`: callback to check if `focusElementSelector` is hidden, only if the walkthrough needs specific verification. By default : `optional`
-   `notScrollOnResize`: do not scroll when resizing (e.g. may be required with dynamic menu on mobile)
-   `observerOptions`: options of DOM detection changes (default: `{ attributes: false, childList: true, subtree: true }`)

**Content**:

-   `contentTemplate`: add a `ng-template` with your description.
-   `contentText`: show a simple description without formating in content.
-   `contentStyle`: background style for content container. Possible values: `none`, `darken`. By default : `darken`.
-   `alignContent`: align the `contentTemplate` horizontally. Possible values: `left`, `center` or `right`. By default : `left`.
-   `verticalAlignContent`: align the `contentTemplate` vertically. Possible values: `above`, `top`, `center`, `bottom` or `below`. By default : `top`.
-   `contentSpacing`: The max space which separates the content to the focus zone horizontally, default is 0 (opposite of the focusZone)
-   `verticalContentSpacing`: The max space which separates the content to the focus zone vertically, default is 50
-   `rootElement`: root element on which walkthrough will scroll to after each positioning, as to avoid hidden zones

**Navigation**:

-   `hidePrevious`: `true` to hide the previous button. By default `false`
-   `previousStep`: add a ling to go to the previous `ng-walkthrough`.
-   `nextStep`: add a ling to go to the next `ng-walkthrough`.
-   `closeButton`: `true` for show the button. By default `false`.
-   `closeAnywhere`: `false` for click anywhere to close. By default `true`.
-   `finishButton`: `true` for show a link to exit. By default `false`.
-   `disabled`: `true` for ignoring the walkthrough based on a boolean flag. By default `false`.
-   `texts`: change texts. It's an overlay of `WalkthroughText`.

**Arrow**:

-   `showArrow`: `true` for show the arrow. By default `false`.
-   `arrowColor`: change the arrow color. By default `#FFF`.

### `ng-walkthrough-flow` attributes

All attributes are optional and not overriding the subcomponents attributes except `previousStep`, `nextStep` that will be ignored.

-   `id`: HTML id.

**Output events**

-   `closed`: fired when a walkthrough has been closed. It sends a boolean value set to true if the walkthrough has been closed with the "finishButton" button.
-   `finished`: fired when the last walkthrough has been closed.

**Focus zone**:

-   `focusHighlightAnimation`: `true` for show highlight animation on the focus element.
-   `focusBackdrop`: `true` for show a dark backdrop around the focus element.
-   `focusGlow`: `true` for show a glow on the focus element.
-   `radius`: apply a “borderRadius” on highlight zone. If `number` the value as change in percent. If `auto` use the focused element borderRadius. If it's a simple `string`, use it without changes.
-   `marginZone`: add a maring of focus zone in px. (e.g. `12 15 12 13` for CSS `12px 15px 12px 13px`, `12 15` for `12px 15px 12px 15px`, `12` for `12px 12px 12px 12px`.)
-   `notScrollOnResize`: do not scroll when resizing (e.g. may be required with dynamic menu on mobile)
-   `observerOptions`: options of DOM detection changes (default: `{ attributes: false, childList: true, subtree: true }`)

**Content**:

-   `contentStyle`: background style for content container. Possible values: `none`, `darken`.
-   `rootElement`: root element on which walkthrough will scroll to after each positioning, as to avoid hidden zones (facultative)

**Navigation**:

-   `hidePrevious`: `true` to hide the previous button. By default `false`
-   `closeButton`: `true` for show the button.
-   `closeAnywhere`: `false` for for click anywhere to close.
-   `texts`: change texts. It's a overlay of `WalkthroughText`.
-   `finishButton`: `true` for show a link to exit. By default `false`. Always `true` on the last step.

**Arrow**:

-   `showArrow`: `true` for show the arrow. By default `false`.
-   `arrowColor`: change the arrow color. By default `#FFF`.

### Change texts

It's possible to change all texts. With the `texts` directive attribute.

```typescript
WalkthroughText {
    previous = 'Previous';
    next     = 'Next';
    close    = 'Close';
}
```

### Statics methods

-   `WalkthroughComponent.walkthroughStop()`: hide and stop the current walkthrough (impossible to open a new walkthrough).
    Does not work if no walkthrough is showed.
-   `WalkthroughComponent.walkthroughContinue()`: show and continue the current walkthrough. Does not work if no walkthrough is paused.
-   `WalkthroughComponent.walkthroughHasShow()`: if the a walkthrough is currently showing.
-   `WalkthroughComponent.walkthroughNext()`: to load the next walkthrough.
-   `WalkthroughComponent.walkthroughPrevious()`: to load the previous walkthrough.

### Statics observable

-   `WalkthroughComponent.onOpen`: on open
-   `WalkthroughComponent.onRefresh`: on reshowing the current step
-   `WalkthroughComponent.onClose`: on close
-   `WalkthroughComponent.onFinish`: on close in the last step
-   `WalkthroughComponent.onNavigate`: on navigate
-   `WalkthroughComponent.onNavigatePrevious`: on navigate on the previous step
-   `WalkthroughComponent.onNavigateNext`: on navigate on the next step

### Example

Highlighting `#selectorId` element with example text in `ng-template`.

```html
<ng-walkthrough
    id="wt-test"
    focusElementSelector="#selectorId"
    focusBackdrop="true"
    [contentTemplate]="template"
    closeButton="true"
>
    <ng-template #template>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit...</p>
    </ng-template>
</ng-walkthrough>
```

Example of scenario with `ng-walkthrough-flow`:

```html
<ng-walkthrough-flow
    #walkFlow
    id="wt-test-flow"
    focusBackdrop="true"
    focusHighlightAnimation="true"
    closeButton="true"
    closeAnywhere="false"
    showArrow="true"
    radius="auto"
    [texts]="frenchText"
>
    <ng-walkthrough
        id="wt-test1-flow"
        focusElementSelector="#test1"
        [contentText]="Lorem ipsum dolor sit amet, consectetur adipiscing elit..."
    >
    </ng-walkthrough>
    <ng-walkthrough
        id="wt-test2-flow"
        focusElementSelector="#test2"
        [contentText]="Lorem ipsum dolor sit amet, consectetur adipiscing elit..."
    >
    </ng-walkthrough>
    <ng-walkthrough
        id="wt-test3-flow"
        focusElementSelector="#test3"
        closeButton="true"
        [contentText]="Lorem ipsum dolor sit amet, consectetur adipiscing elit..."
    >
    </ng-walkthrough>
</ng-walkthrough-flow>
```

For more examples, see `examples/example.component.html`.

## Publishing the library

```
npm run build:lib
cd dist/angular-walkthrough
npm publish
```

## License

Like Angular, this module is released under the permissive MIT license. Your contributions are always welcome.
