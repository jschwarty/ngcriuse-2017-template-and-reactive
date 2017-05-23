#### Reactive
```html
<form [formGroup]="form"
  (ngSubmit)="onSubmit(form.value)">
  . . .
</form>
```
<br/>
<strong>FormGroup Directive</strong>
```typescript
@Output() ngSubmit = new EventEmitter();
```