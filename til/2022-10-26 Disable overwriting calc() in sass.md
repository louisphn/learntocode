Reference: https://stackoverflow.com/questions/52869421/sass-calc-vs-normal-calculation

SASS calculation is made on compilation. While CSS calc() is always made on the browser. For example:

SASS height: 100px / 2; will compile to height: 50px; <- and this is what the browser will see always no matter what.

CSS width: calc(100% - 20px) will always be this even on the browser, and at that point the browser will do the calculations depending on what that 100% looks like.

In order to make SASS calculation not overwrite CSS calc() we need to use the string interpolation:

```css
// will compile to number (〇〇vw)
height: calc({470} * calc(100vw / 375));

// will compile to calc(470 * calc(100vw / 375))
height: calc(#{470} * calc(100vw / #{375}));
```
