<h4 class="miami template">Template</h4>
```html
<form #form="ngForm"
  (ngSubmit)="onSubmit(form.value)">
  . . .
</form>
```
<br/>
<strong>NgForm Directive</strong>
```typescript
outputs: ['ngSubmit']
```