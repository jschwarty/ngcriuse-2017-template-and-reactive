<h4 class="miami template">Template</h4>
```html
<form>
  . . .
</form>
```
<h4 class="miami">NgForm Directive</h4>
```typescript
selector: `
  form:not([ngNoForm]):not([formGroup]),
  ngForm, [ngForm]`

constructor(. . .) {
  this.form = new FormGroup({}, . . .});
}
```