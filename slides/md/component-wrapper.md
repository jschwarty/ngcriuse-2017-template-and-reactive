#### Form Field Wrapper
```html
<!-- Template approach -->
<app-name-field><input type="text" ngModel name="nickname"></app-name-field>
<!-- Reactive approach -->
<app-name-field><input type="text" formControlName="nickname"></app-name-field>
```

```typescript
@Component({
  selector: 'app-name-field',
  template: `<ng-content></ng-content><div *ngIf="inUse">Nickname in use!</div>`
})
export class NameFieldComponent implements AfterContentInit {
  @ContentChild(NgControl) control;
  inUse = false;

  ngAfterContentInit(): void {
    this.control.valueChanges
        .subscribe(value => {this.inUse = value.toLowerCase() === 'schwarty';});
  }
}
```