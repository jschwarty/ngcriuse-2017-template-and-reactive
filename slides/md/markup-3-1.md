#### Template
```html
<form #form="ngForm"
  (ngSubmit)="onSubmit(form.value)">
  . . .
</form>
```