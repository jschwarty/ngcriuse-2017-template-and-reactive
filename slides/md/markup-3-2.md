<h4 class="miami reactive">Reactive</h4>
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