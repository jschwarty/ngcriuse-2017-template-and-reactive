#### Parent of Custom Form Component (with validator)
```html
<!-- Template approach -->
<app-color ngModel name="color" pattern=""></app-color>

<!-- Reactive approach -->
<app-color formControlName="color" pattern=""></app-color>
```

#### Custom Form Component (with NgControl)
```typescript
export class ColorComponent {
  @ContentChild(NgControl) control;
  . . .
}

template: `<label [class.invalid]="control.invalid">
              <input type="text" (keyup)="onChange($event)" (blur)="onBlur()"
                 [value]="value">
            </label>`
```