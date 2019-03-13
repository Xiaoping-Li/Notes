(https://developer.mozilla.org/en-US/docs/Web/CSS/animation)
# CSS Animation
## Animation properties
**Animation properties**: control how the animation should behave. There are eight animation properties in total.
  * animation-name: sets the **name** of the animation, which is later used by **@keyframes** to tell CSS which rules go with which animations
  * animation-duration: sets the **length of time** for the animation 
  * animation-timing-function: controls how quickly an animated element changes over the duration of the animation (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function) 
       * ease: the default value, which starts slow, speeds up in the middle, and then slows down again in the end. 
       * ease-out: which is quick in the beginning then slows down, 
       * ease-in: which is slow in the beginning, then speeds up at the end, 
       * linear: which applies a constant animation speed throughout.
  * animation-delay, 
  * animation-iteration-count: allows you to control how many `times` you would like to `loop through` the animation.
       * infinite: The animation will repeat forever.
       * number: The number of times the animation will repeat; this is 1 by default. You may specify non-integer values to play part of an animation cycle: for example, 0.5 will play half of the animation cycle. Negative values are invalid.
  * animation-direction, 
  * animation-fill-mode: specifies the style applied to an element when the animation has finished. (https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode)
       * none
       * forwards
       * backwords
       * both
  * animation-play-state.
## @keyframes rule 
**@keyframes rule**: controls what happens during that animation.
## Examples
```
HTML
<div id="animExample"></div>
```
### 1. Continually changing background-color
```
#animExample {
  animation-name: rainbow;
  animation-duration: 3s;
}

@keyframes rainbow {
  0% {
    background-color: red;
  }
  50% {
    background-color: yellow;
  }
  100% {
    background-color: yellow;
  }
}
```
### 2. Chaning div size when hover
```
#animExample:hover {
  animation-name: expand;
  animation-duration: 500ms;
}

@keyframes expand {
  100% {
    width: 350px;
    height: 100px;
  }
}
```
### 3. Using animation-fill-mode CSS property sets how a CSS animation applies styles to its target before and after its execution.
```
#animExample:hover {
  animation-name: expand;
  animation-duration: 500ms;
  animation-fill-mode: forwards;
}
```
### 4. Creating movement
When elements have a specified position, such as `fixed` or `relative`, the CSS _offset properties_ `right, left, top, and bottom` can be used in animation rules to create movement.
As shown in the example below, we can push the item downwards then upwards by setting the top property of the 50% keyframe to 50px, but having it set to 0px for the first (0%) and the last (100%) keyframe.
```
@keyframes rainbow {
  0% {
    background-color: blue;
    top: 0px;
  }
  50% {
    background-color: green;
    top: 50px;
  }
  100% {
    background-color: yellow;
    top: 0px;
  }
}
```
### 5.















