#### Template
```html
<input type="text" name="nickname"
  [(ngForm)]="model.nickname"
  required
  pattern="^[a-zA-Z0-9]*$">
```