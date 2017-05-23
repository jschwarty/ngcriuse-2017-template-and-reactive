#### Template
```html
<input type="text" name="nickname"
  [(ngModel)]="model.nickname"
  required
  pattern="^[a-zA-Z0-9]*$"
  #nickname="ngModel">
  
<div *ngIf="nickname
              .hasError('pattern')">
  Nickname must be alphanumeric
</div>
```