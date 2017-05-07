#### Reactive
```typescript
@Component({
  selector: '[appForm]',
  . . .
})
export class FormComponent {
  constructor(
    private dataService: DataService) {}
    
  onSubmit(formValue) {
    this.dataService.save(formValue);
  }
}
```