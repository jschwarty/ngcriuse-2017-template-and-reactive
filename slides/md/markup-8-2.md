<h4 class="miami reactive">Reactive</h4>
```html
<input type="text"
  formControlName="nickname"
  required
  pattern="^[a-zA-Z0-9]*$">
  
  
<div *ngIf="form.get('nickname')
              .hasError('pattern')">
  Nickname must be alphanumeric
</div>
```