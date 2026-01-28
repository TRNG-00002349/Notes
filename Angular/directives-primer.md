# Angular Directives Overview

## What Are Directives?

Directives are instructions in the DOM that tell Angular how to manipulate elements, components, or attributes.

## Three Types of Directives

1. **Component Directives** - Directives with templates (components are directives)
2. **Structural Directives** - Change DOM layout by adding/removing elements
3. **Attribute Directives** - Change appearance or behavior of elements

## Structural Directives

Modify DOM structure. Always prefixed with `*`.

**ngIf** - Conditionally add/remove elements
```typescript
<div *ngIf="isLoggedIn">Welcome back!</div>
<div *ngIf="user; else loading">{{ user.name }}</div>

<ng-template #loading>Loading...</ng-template>
```

**ngFor** - Loop through collections
```typescript
<li *ngFor="let item of items">{{ item }}</li>
<li *ngFor="let item of items; index as i">{{ i }}: {{ item }}</li>
<li *ngFor="let item of items; first as isFirst">
  <span [class.bold]="isFirst">{{ item }}</span>
</li>
```

**ngSwitch** - Multi-case conditionals
```typescript
<div [ngSwitch]="status">
  <p *ngSwitchCase="'active'">Active</p>
  <p *ngSwitchCase="'pending'">Pending</p>
  <p *ngSwitchDefault>Unknown</p>
</div>
```

## Attribute Directives

Modify element behavior or appearance.

**ngClass** - Add/remove CSS classes
```typescript
<div [ngClass]="'highlight'">Text</div>
<div [ngClass]="['class1', 'class2']">Text</div>
<div [ngClass]="{ 'active': isActive, 'disabled': !isEnabled }">Text</div>
```

**ngStyle** - Apply inline styles
```typescript
<div [ngStyle]="{ 'color': textColor }">Text</div>
<div [ngStyle]="{ 'font-size.px': fontSize, 'color': textColor }">Text</div>
```

**ngModel** - Two-way data binding
```typescript
<input [(ngModel)]="username">
<p>Hello {{ username }}</p>
```

## Custom Attribute Directive

```typescript
import { Directive, ElementRef, HostListener } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor(private el: ElementRef) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.el.nativeElement.style.backgroundColor = 'yellow';
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.el.nativeElement.style.backgroundColor = '';
  }
}
```

Use it:
```typescript
<p appHighlight>Hover over me!</p>
```

## Custom Structural Directive

```typescript
import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[appUnless]'
})
export class UnlessDirective {
  @Input() set appUnless(condition: boolean) {
    if (!condition) {
      this.viewContainer.createEmbeddedView(this.templateRef);
    } else {
      this.viewContainer.clear();
    }
  }

  constructor(
    private templateRef: TemplateRef<any>,
    private viewContainer: ViewContainerRef
  ) {}
}
```

Use it:
```typescript
<div *appUnless="isLoggedIn">Please log in</div>
```

## Key Points

- Structural directives use `*` prefix and manipulate DOM structure
- Attribute directives modify element properties/appearance
- Built-in directives handle most common scenarios
- Custom directives extend Angular's capabilities for specialized needs
