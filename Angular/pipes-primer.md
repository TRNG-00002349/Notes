# Angular Pipes Overview

## What Are Pipes?

Pipes transform data in your templates. They take input values and return formatted output values.

## Basic Syntax

```typescript
{{ value | pipeName }}
{{ value | pipeName:parameter }}
{{ value | pipe1 | pipe2 }}  // Chain pipes
```

## Common Built-in Pipes

**DatePipe** - Format dates
```typescript
{{ today | date:'short' }}  // 1/28/26, 3:45 PM
{{ today | date:'fullDate' }}  // Wednesday, January 28, 2026
```

**CurrencyPipe** - Format currency
```typescript
{{ price | currency }}  // $123.45
{{ price | currency:'EUR' }}  // €123.45
```

**DecimalPipe** - Format numbers
```typescript
{{ pi | number:'1.2-2' }}  // 3.14
```

**PercentPipe** - Format percentages
```typescript
{{ ratio | percent }}  // 75%
```

**UpperCasePipe / LowerCasePipe** - Transform text
```typescript
{{ name | uppercase }}  // JOHN
{{ name | lowercase }}  // john
```

**JsonPipe** - Debug objects
```typescript
{{ user | json }}  // Displays object as JSON
```

## Custom Pipes

Create your own pipe:

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'reverse'
})
export class ReversePipe implements PipeTransform {
  transform(value: string): string {
    return value.split('').reverse().join('');
  }
}
```

Use it:
```typescript
{{ 'hello' | reverse }}  // olleh
```

## Pure vs Impure Pipes

**Pure pipes** (default) - Only re-run when input reference changes
**Impure pipes** - Re-run on every change detection cycle

```typescript
@Pipe({
  name: 'myPipe',
  pure: false  // Makes it impure
})
```

## Key Points

- Pipes are declarative and keep templates clean
- Chain multiple pipes for complex transformations
- Built-in pipes cover most common formatting needs
- Custom pipes are simple to create for specialized logic
