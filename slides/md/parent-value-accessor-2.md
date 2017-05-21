#### Parent of Custom Form Component (with validator)
```html
<!-- Template approach -->
<app-color ngModel name="color" pattern="^[a-zA-Z0-9]*$"></app-color>

<!-- Reactive approach -->
<app-color formControlName="color" pattern="^[a-zA-Z0-9]*$"></app-color>
```

#### Custom Form Component (with NgControl)
```typescript
export class ColorComponent {
  @ContentChild(NgControl) control;
  . . .
}

template: `<input type="text" (keyup)="onChange($event)" (blur)="onBlur()"
              [value]="value"
              [class.invalid-pattern]="control.hasError('pattern')">`
```