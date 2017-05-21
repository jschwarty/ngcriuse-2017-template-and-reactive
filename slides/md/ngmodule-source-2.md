#### Reactive
```typescript
REACTIVE_DRIVEN_DIRECTIVES
  FormControlDirective
  FormGroupDirective
  FormControlName
  FormGroupName
  FormArrayName


@NgModule({
  declarations: 
    [REACTIVE_DRIVEN_DIRECTIVES],
  exports: [
    InternalFormsSharedModule,
    REACTIVE_DRIVEN_DIRECTIVES
  ],
  . . .
})
export class ReactiveFormsModule { }
```
