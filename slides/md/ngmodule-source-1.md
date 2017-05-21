#### Template
```typescript
TEMPLATE_DRIVEN_DIRECTIVES
  NgModel
  NgModelGroup
  NgForm




@NgModule({
  declarations: 
    [TEMPLATE_DRIVEN_DIRECTIVES],
  exports: [
    InternalFormsSharedModule,
    TEMPLATE_DRIVEN_DIRECTIVES
  ],
  . . .
})
export class FormsModule { }
```
