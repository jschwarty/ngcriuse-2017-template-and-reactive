#### Form Field Wrapper Component
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