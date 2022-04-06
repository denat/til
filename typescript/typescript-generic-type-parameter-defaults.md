# Generic type parameters can have defaults

Since TypeScript 2.2, generic type parameters can have defaults too. 

```typescript
class Employee<IdentifierType = string> {
  id: IdentifierType;

  constructor(id: IdentifierType) {
    this.id = id;
  }
}

const winterfellEmployee1 = new Employee("W01");
const winterfellEmployee2 = new Employee("W02");

// Highgarden prefers numbers to identify their employees
const highgardenEmployee1 = new Employee<number>(1);
const highgardenEmployee2 = new Employee<number>(2);
```