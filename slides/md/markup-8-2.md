#### Reactive
```html
<input type="text"
  formControlName="nickname"
  required
  pattern="^[a-zA-Z0-9]*$">
  
  
<div *ngIf="form.get('nickname')
              .hasError('required')">
  Nickname is required
</div>
```