<h4 class="miami reactive">Reactive</h4>
```html
<form [formGroup]="form"
  (ngSubmit)="onSubmit(form.value)">
  . . .
</form>
```
<h4 class="miami">FormGroup Directive</h4>
```typescript
@Output() ngSubmit = new EventEmitter();
```