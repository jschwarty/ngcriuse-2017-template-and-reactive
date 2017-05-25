<h4 class="miami">Custom Validator Directive</h4>
```typescript
@Directive({
  selector: `[appNickUnique][ngModel], 
             [appNickUnique][formControl], [appNickUnique][formControlName]`,
  providers: [{
      provide: NG_VALIDATORS, multi: true,
      useExisting: forwardRef(() => NickUniqueDirective)
    }]
})
export class NickUniqueDirective implements Validator {
  validate(c: AbstractControl): ValidationErrors | any { /* validation logic */ }
}
```

```html
<!-- Template approach -->
<input type="text" ngModel name="nickname" appNickUnique>
<!-- Reactive approach -->
<input type="text" formControlName="nickname" appNickUnique>
```