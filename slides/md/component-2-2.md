#### Reactive
```typescript
form: FormGroup;

constructor(
  private dataService: DataService,
  private formBuilder: FormBuilder) {

  this.form = this.formBuilder.group({
    nickname: ''
  });
}
```