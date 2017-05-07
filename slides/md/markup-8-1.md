#### Template
```html
<input type="text" name="nickname"
  [(ngForm)]="model.nickname"
  required
  pattern="^[a-zA-Z0-9]*$"
  #nickname="ngModel">
  
<div *ngIf="nickname
              .hasError('required')">
  Nickname is required
</div>
```