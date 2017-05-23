#### Form Field Wrapper Component
```html
<!-- Template approach -->
<app-name-field>
  <input type="text" ngModel name="nickname">
</app-name-field>

<!-- Reactive approach -->
<app-name-field>
  <input type="text" formControlName="nickname">
</app-name-field>
```