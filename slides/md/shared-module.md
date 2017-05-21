```typescript
SHARED_FORM_DIRECTIVES
  NgNoValidate, NgSelectOption, NgSelectMultipleOption,
  DefaultValueAccessor, NumberValueAccessor, RangeValueAccessor,
  CheckboxControlValueAccessor, SelectControlValueAccessor,
  SelectMultipleControlValueAccessor, RadioControlValueAccessor,
  NgControlStatus, NgControlStatusGroup, RequiredValidator,
  MinValidator, MinLengthValidator, MaxValidator, MaxLengthValidator, 
  PatternValidator, CheckboxRequiredValidator, EmailValidator
  
/**
 * Internal module used for sharing directives 
 * between FormsModule and ReactiveFormsModule
 */
@NgModule({
  declarations: SHARED_FORM_DIRECTIVES,
  exports: SHARED_FORM_DIRECTIVES,
})
export class InternalFormsSharedModule { }
```