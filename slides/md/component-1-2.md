<h4 class="miami reactive">Reactive</h4>
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