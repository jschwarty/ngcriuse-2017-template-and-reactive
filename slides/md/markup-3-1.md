<h4 class="miami template">Template</h4>
```html
<form #form="ngForm"
  (ngSubmit)="onSubmit(form.value)">
  . . .
</form>
```
<h4 class="miami">NgForm Directive</h4>
```typescript
outputs: ['ngSubmit']
```