#### Reactive
```html
<form [formGroup]="form"
  (ngSubmit)="onSubmit(form.value)">
  . . .
</form>
```