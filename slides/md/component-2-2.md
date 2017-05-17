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
<p class="fragment" data-fragment-index="0" data-code-focus="5"></p>
<p class="fragment" data-fragment-index="1" data-code-focus="7-9"></p>