# CSS Animation
## Animation properties
**Animation properties**: control how the animation should behave. There are eight animation properties in total.
  * animation-name: sets the **name** of the animation, which is later used by **@keyframes** to tell CSS which rules go with which animations. 
  * animation-duration: sets the **length of time** for the animation. 
  ```
                        
  ```
  * animation-timing-function, 
  * animation-delay, 
  * animation-iteration-count, 
  * animation-direction, 
  * animation-fill-mode,
  * animation-play-state.
## @keyframes rule 
**@keyframes rule**: controls what happens during that animation.
## Examples
```
HTML
<div id="animExample"></div>
```
### Continually changing background-color
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
