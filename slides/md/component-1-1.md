#### Template
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