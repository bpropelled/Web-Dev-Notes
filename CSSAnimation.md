# CSS Animation

## Simple Example 
```css
@keyframes name-of-animation {
  0%   {transform: translateY(0)}
  25%  {transform: translateY(-25px)}
  75%  {transform: translateY(25px)}
  100% {transform: translateY(0)}
}

.item-to-animate {
  animation: name-of-animation 5s linear infinite;
}

```