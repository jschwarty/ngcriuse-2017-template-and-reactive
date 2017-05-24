<h4 class="miami reactive">Reactive</h4>
```html
<input type="text"
  formControlName="nickname">
```
<p>or</p>
```html
<input type="text"
  [formControl]="form.get('nickname')">
```