<h4 class="miami reactive">Reactive</h4>
```html
<input type="text"
  formControlName="nickname">
```
<h4 class="miami">or</h4>
```html
<input type="text"
  [formControl]="form.get('nickname')">
```