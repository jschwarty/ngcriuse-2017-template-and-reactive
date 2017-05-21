#### Custom Directive
```typescript
@Directive({
  selector: `[appNicknameUnique][formControl], 
             [appNicknameUnique][formControlName], 
             [appNicknameUnique][ngModel]`,
  providers: [{
      provide: NG_VALIDATORS, multi: true,
      useExisting: forwardRef(() => NicknameUniqueDirective)
    }]
})
export class NicknameUniqueDirective implements Validator {
  validate(c: AbstractControl): ValidationErrors | any { /* validation logic */ }
}
```