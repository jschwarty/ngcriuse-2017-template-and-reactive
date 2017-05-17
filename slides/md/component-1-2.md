#### Reactive
```typescript
export class FormComponent {
  constructor(
    private dataService: DataService) {
  }
    
  onSubmit(formValue) {
    this.dataService.save(formValue);
  }
}
```
<p class="fragment" data-fragment-index="0" data-code-focus="3"></p>
<p class="fragment" data-fragment-index="1" data-code-focus="7"></p>