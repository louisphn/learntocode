Change box color and text color of autofill input field:
Source: https://stackoverflow.com/questions/2781549/removing-input-background-colour-for-chrome-autocomplete

```css
/* browser autofill input field */
input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
input:-webkit-autofill:active {
  /* change field color */
  -webkit-box-shadow: 0 0 0 30px #262833 inset !important;
  /* change text color */
  -webkit-text-fill-color: #fffefd !important;
}
```
