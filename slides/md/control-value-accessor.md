#### Custom Form Component
```typescript
@Component({
  selector: 'app-color',
  template: `<input type="text" (keyup)="onChange($event)" (blur)="onBlur()"
                [value]="value">`,
  providers: [{
      provide: NG_VALUE_ACCESSOR, multi: true,
      useExisting: forwardRef(() => ColorComponent)
    }]
})
export class ColorComponent {
  private onChangeCallback, onTouchedCallback;
  value;
  onChange(el) { this.onChangeCallback(el.nativeElement.value); }
  onBlur() { this.onTouchedCallback(); }
  writeValue(value: any) { this.value = value; }
  registerOnChange(fn: any) { this.onChangeCallback = fn; }
  registerOnTouched(fn: any) { this.onTouchedCallback = fn; }
}
```