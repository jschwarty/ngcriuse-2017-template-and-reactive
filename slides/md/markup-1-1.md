<h4 class="miami template">Template</h4>
```html
<form>
  . . .
</form>
```
<br/>
<strong>NgForm Directive</strong>
```typescript
selector: `
  form:not([ngNoForm]):not([formGroup]),
  ngForm, [ngForm]`

constructor(validators, asyncValidators) {
  this.form = new FormGroup({}, 
   composeValidators(validators), 
   composeAsyncValidators(asyncValidators));
}
```