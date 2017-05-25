<h4 class="miami">Form Field Wrapper Component</h4>
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