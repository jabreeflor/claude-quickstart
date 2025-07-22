# Angular Component Scaffold

## Task

**Scaffold a modern Angular component following latest best practices using context7 research**

This command creates a complete Angular component with modern patterns, version-agnostic compatibility, and comprehensive testing setup.

## Instructions

- Analyze the current Angular project to detect version and configuration
- Use context7 to verify latest Angular best practices and patterns
- Generate component files following current conventions and architecture
- Include proper TypeScript patterns, signal-based reactivity, and accessibility
- Create comprehensive unit tests with modern testing patterns
- Ensure version compatibility across Angular 14+ with graceful fallbacks

## Component Generation Strategy

1. **Project Analysis**: Detect Angular version, architecture (standalone vs modules), and project structure
2. **Best Practices Research**: Use context7 to verify current Angular recommendations
3. **Template Selection**: Choose appropriate patterns based on version support
4. **File Generation**: Create component, template, styles, and test files
5. **Integration**: Wire up imports, routing, and dependencies as needed

## Version Detection & Compatibility

### **Angular Version Support**
- **Angular 17+**: Standalone components, signals, modern inject()
- **Angular 16+**: Signals available, standalone components stable
- **Angular 14-15**: inject() function, standalone components experimental
- **Angular 12-13**: Traditional patterns with modern TypeScript

### **Feature Detection Logic**
```typescript
// Detect project capabilities
const supportsSignals = angularVersion >= 16;
const supportsStandalone = angularVersion >= 15;
const supportsInjectFunction = angularVersion >= 14;
const supportsControlFlow = angularVersion >= 17;
```

## File Structure Template

```
component-name/
├── component-name.component.ts      # Main component class
├── component-name.component.html    # Template
├── component-name.component.scss    # Styles
├── component-name.component.spec.ts # Unit tests
└── index.ts                        # Barrel export (optional)
```

## Component Template (Version-Agnostic)

```typescript
import { 
  Component, 
  ChangeDetectionStrategy,
  {{#if supportsInjectFunction}}inject,{{/if}}
  {{#if supportsSignals}}signal, computed,{{/if}}
  {{#if traditionalReactive}}OnInit, OnDestroy,{{/if}}
} from '@angular/core';
{{#if isStandalone}}
import { CommonModule } from '@angular/common';
import { ReactiveFormsModule } from '@angular/forms';
{{/if}}
{{#if traditionalReactive}}
import { Subject, BehaviorSubject } from 'rxjs';
import { takeUntil } from 'rxjs/operators';
{{/if}}

@Component({
  selector: 'app-{{kebab-case-name}}',
  {{#if isStandalone}}
  standalone: true,
  imports: [
    CommonModule,
    ReactiveFormsModule,
    // Add other imports as needed
  ],
  {{/if}}
  templateUrl: './{{kebab-case-name}}.component.html',
  styleUrls: ['./{{kebab-case-name}}.component.scss'],
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class {{PascalCaseName}} {{#if traditionalReactive}}implements OnInit, OnDestroy{{/if}} {
  {{#if supportsSignals}}
  // Signal-based reactive state (Angular 16+)
  readonly data = signal<{{DataType}}[]>([]);
  readonly loading = signal(false);
  readonly error = signal<string | null>(null);
  
  // Computed values
  readonly filteredData = computed(() => 
    this.data().filter(item => item.active)
  );
  {{else}}
  // Traditional reactive patterns
  private readonly destroy$ = new Subject<void>();
  readonly data$ = new BehaviorSubject<{{DataType}}[]>([]);
  readonly loading$ = new BehaviorSubject<boolean>(false);
  readonly error$ = new BehaviorSubject<string | null>(null);
  {{/if}}

  {{#if supportsInjectFunction}}
  // Modern dependency injection (Angular 14+)
  private readonly {{serviceName}} = inject({{ServiceClass}});
  private readonly router = inject(Router);
  {{else}}
  // Traditional constructor injection
  constructor(
    private {{serviceName}}: {{ServiceClass}},
    private router: Router
  ) {}
  {{/if}}

  {{#if traditionalReactive}}
  ngOnInit(): void {
    this.loadInitialData();
  }

  ngOnDestroy(): void {
    this.destroy$.next();
    this.destroy$.complete();
  }
  {{/if}}

  // Component methods
  {{#if supportsSignals}}
  loadData(): void {
    this.loading.set(true);
    this.error.set(null);
    
    this.{{serviceName}}.getData().subscribe({
      next: (data) => {
        this.data.set(data);
        this.loading.set(false);
      },
      error: (error) => {
        this.error.set(error.message);
        this.loading.set(false);
      }
    });
  }

  onItemClick(item: {{DataType}}): void {
    // Handle item selection
    console.log('Selected item:', item);
  }

  onAddItem(): void {
    const newItem: {{DataType}} = {
      // Create new item
    };
    this.data.update(current => [...current, newItem]);
  }
  {{else}}
  private loadInitialData(): void {
    this.loading$.next(true);
    this.{{serviceName}}.getData()
      .pipe(takeUntil(this.destroy$))
      .subscribe({
        next: (data) => {
          this.data$.next(data);
          this.loading$.next(false);
        },
        error: (error) => {
          this.error$.next(error.message);
          this.loading$.next(false);
        }
      });
  }
  {{/if}}
}
```

## Template Structure (component.html)

```html
{{#if supportsControlFlow}}
<!-- Angular 17+ Control Flow -->
<div class="{{kebab-case-name}}">
  <header class="{{kebab-case-name}}__header">
    <h2>{{ComponentTitle}}</h2>
    <button 
      type="button"
      class="btn btn--primary"
      (click)="onAddItem()"
      [attr.aria-label]="'Add new ' + componentType">
      Add Item
    </button>
  </header>

  <main class="{{kebab-case-name}}__content">
    @if (loading()) {
      <div class="loading-spinner" role="status" aria-label="Loading data">
        Loading...
      </div>
    } @else if (error()) {
      <div class="error-message" role="alert">
        {{ error() }}
      </div>
    } @else {
      <div class="items-grid">
        @for (item of filteredData(); track item.id) {
          <div 
            class="item-card"
            (click)="onItemClick(item)"
            [attr.aria-label]="'Select ' + item.name"
            role="button"
            tabindex="0">
            <h3>{{ item.name }}</h3>
            <p>{{ item.description }}</p>
          </div>
        } @empty {
          <div class="empty-state">
            <p>No items available</p>
          </div>
        }
      </div>
    }
  </main>
</div>
{{else}}
<!-- Traditional Angular template syntax -->
<div class="{{kebab-case-name}}">
  <header class="{{kebab-case-name}}__header">
    <h2>{{ComponentTitle}}</h2>
    <button 
      type="button"
      class="btn btn--primary"
      (click)="onAddItem()"
      [attr.aria-label]="'Add new ' + componentType">
      Add Item
    </button>
  </header>

  <main class="{{kebab-case-name}}__content">
    <div *ngIf="loading$ | async" class="loading-spinner" role="status">
      Loading...
    </div>
    
    <div *ngIf="error$ | async as error" class="error-message" role="alert">
      {{ error }}
    </div>
    
    <div *ngIf="!(loading$ | async) && !(error$ | async)" class="items-grid">
      <div 
        *ngFor="let item of data$ | async; trackBy: trackByItemId"
        class="item-card"
        (click)="onItemClick(item)"
        [attr.aria-label]="'Select ' + item.name"
        role="button"
        tabindex="0">
        <h3>{{ item.name }}</h3>
        <p>{{ item.description }}</p>
      </div>
      
      <div *ngIf="(data$ | async)?.length === 0" class="empty-state">
        <p>No items available</p>
      </div>
    </div>
  </main>
</div>
{{/if}}
```

## SCSS Structure (component.scss)

```scss
.{{kebab-case-name}} {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-lg, 1.5rem);
  padding: var(--spacing-md, 1rem);

  &__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid var(--color-border, #e0e0e0);
    padding-bottom: var(--spacing-sm, 0.5rem);

    h2 {
      margin: 0;
      color: var(--color-text-primary, #333);
      font-size: var(--font-size-lg, 1.25rem);
    }
  }

  &__content {
    flex: 1;
    min-height: 200px;
  }

  .loading-spinner {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 200px;
    color: var(--color-text-secondary, #666);
  }

  .error-message {
    padding: var(--spacing-md, 1rem);
    background-color: var(--color-error-bg, #fee);
    color: var(--color-error, #c33);
    border: 1px solid var(--color-error-border, #fcc);
    border-radius: var(--border-radius, 4px);
  }

  .items-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: var(--spacing-md, 1rem);
  }

  .item-card {
    padding: var(--spacing-md, 1rem);
    border: 1px solid var(--color-border, #e0e0e0);
    border-radius: var(--border-radius, 4px);
    cursor: pointer;
    transition: all 0.2s ease;

    &:hover {
      border-color: var(--color-primary, #007bff);
      transform: translateY(-2px);
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }

    &:focus {
      outline: 2px solid var(--color-focus, #007bff);
      outline-offset: 2px;
    }

    h3 {
      margin: 0 0 var(--spacing-sm, 0.5rem) 0;
      color: var(--color-text-primary, #333);
    }

    p {
      margin: 0;
      color: var(--color-text-secondary, #666);
      line-height: 1.5;
    }
  }

  .empty-state {
    text-align: center;
    padding: var(--spacing-xl, 2rem);
    color: var(--color-text-secondary, #666);
  }

  .btn {
    padding: var(--spacing-sm, 0.5rem) var(--spacing-md, 1rem);
    border: none;
    border-radius: var(--border-radius, 4px);
    cursor: pointer;
    font-size: var(--font-size-base, 1rem);
    transition: all 0.2s ease;

    &--primary {
      background-color: var(--color-primary, #007bff);
      color: var(--color-primary-contrast, white);

      &:hover {
        background-color: var(--color-primary-dark, #0056b3);
      }

      &:focus {
        outline: 2px solid var(--color-focus, #007bff);
        outline-offset: 2px;
      }
    }
  }
}

// Responsive design
@media (max-width: 768px) {
  .{{kebab-case-name}} {
    &__header {
      flex-direction: column;
      gap: var(--spacing-sm, 0.5rem);
      align-items: stretch;
    }

    .items-grid {
      grid-template-columns: 1fr;
    }
  }
}
```

## Test Template (component.spec.ts)

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
{{#if supportsSignals}}
import { signal } from '@angular/core';
{{/if}}
import { {{PascalCaseName}} } from './{{kebab-case-name}}.component';
{{#if hasService}}
import { {{ServiceClass}} } from '../services/{{service-file-name}}.service';
{{/if}}
import { of, throwError } from 'rxjs';

describe('{{PascalCaseName}}', () => {
  let component: {{PascalCaseName}};
  let fixture: ComponentFixture<{{PascalCaseName}}>;
  {{#if hasService}}
  let mockService: jasmine.SpyObj<{{ServiceClass}}>;
  {{/if}}

  beforeEach(async () => {
    {{#if hasService}}
    mockService = jasmine.createSpyObj('{{ServiceClass}}', ['getData']);
    {{/if}}

    await TestBed.configureTestingModule({
      {{#if isStandalone}}
      imports: [{{PascalCaseName}}],
      {{else}}
      declarations: [{{PascalCaseName}}],
      {{/if}}
      {{#if hasService}}
      providers: [
        { provide: {{ServiceClass}}, useValue: mockService }
      ]
      {{/if}}
    }).compileComponents();

    fixture = TestBed.createComponent({{PascalCaseName}});
    component = fixture.componentInstance;
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  {{#if supportsSignals}}
  describe('Signal-based functionality', () => {
    it('should initialize with empty data', () => {
      expect(component.data()).toEqual([]);
      expect(component.loading()).toBe(false);
      expect(component.error()).toBeNull();
    });

    it('should update data signal', () => {
      const testData = [{ id: 1, name: 'Test', active: true }];
      component.data.set(testData);
      
      expect(component.data()).toEqual(testData);
      expect(component.filteredData()).toEqual(testData);
    });

    it('should filter active items in computed signal', () => {
      const testData = [
        { id: 1, name: 'Active', active: true },
        { id: 2, name: 'Inactive', active: false }
      ];
      component.data.set(testData);
      
      expect(component.filteredData()).toEqual([testData[0]]);
    });

    {{#if hasService}}
    it('should handle successful data loading', () => {
      const testData = [{ id: 1, name: 'Test', active: true }];
      mockService.getData.and.returnValue(of(testData));
      
      component.loadData();
      
      expect(component.loading()).toBe(false);
      expect(component.data()).toEqual(testData);
      expect(component.error()).toBeNull();
    });

    it('should handle error during data loading', () => {
      const errorMessage = 'Failed to load data';
      mockService.getData.and.returnValue(throwError(() => new Error(errorMessage)));
      
      component.loadData();
      
      expect(component.loading()).toBe(false);
      expect(component.error()).toBe(errorMessage);
    });
    {{/if}}
  });
  {{else}}
  describe('Traditional reactive functionality', () => {
    it('should initialize observables', () => {
      component.data$.subscribe(data => {
        expect(data).toEqual([]);
      });
    });

    {{#if hasService}}
    it('should load initial data on init', () => {
      const testData = [{ id: 1, name: 'Test', active: true }];
      mockService.getData.and.returnValue(of(testData));
      
      component.ngOnInit();
      
      component.data$.subscribe(data => {
        expect(data).toEqual(testData);
      });
    });
    {{/if}}
  });
  {{/if}}

  describe('User interactions', () => {
    it('should handle item click', () => {
      const testItem = { id: 1, name: 'Test', active: true };
      spyOn(console, 'log');
      
      component.onItemClick(testItem);
      
      expect(console.log).toHaveBeenCalledWith('Selected item:', testItem);
    });

    {{#if supportsSignals}}
    it('should add new item', () => {
      const initialCount = component.data().length;
      
      component.onAddItem();
      
      expect(component.data().length).toBe(initialCount + 1);
    });
    {{/if}}
  });

  describe('Template integration', () => {
    it('should render component title', () => {
      fixture.detectChanges();
      const titleElement = fixture.nativeElement.querySelector('h2');
      expect(titleElement?.textContent).toContain('{{ComponentTitle}}');
    });

    it('should have accessible button', () => {
      fixture.detectChanges();
      const button = fixture.nativeElement.querySelector('button');
      expect(button?.getAttribute('aria-label')).toBeTruthy();
    });
  });

  describe('Accessibility', () => {
    it('should have proper ARIA attributes', () => {
      fixture.detectChanges();
      const loadingSpinner = fixture.nativeElement.querySelector('.loading-spinner');
      if (loadingSpinner) {
        expect(loadingSpinner.getAttribute('role')).toBe('status');
      }
    });

    it('should have keyboard navigation support', () => {
      fixture.detectChanges();
      const itemCards = fixture.nativeElement.querySelectorAll('.item-card');
      itemCards.forEach((card: HTMLElement) => {
        expect(card.getAttribute('tabindex')).toBe('0');
        expect(card.getAttribute('role')).toBe('button');
      });
    });
  });
});
```

## Scaffolding Actions

1. **Detect Angular Environment**
   - Read `angular.json` and `package.json`
   - Identify Angular version and project structure
   - Determine standalone vs module architecture

2. **Generate Component Files**
   - Create TypeScript component with version-appropriate patterns
   - Generate responsive HTML template with accessibility
   - Create SCSS with CSS custom properties and responsive design
   - Generate comprehensive unit tests

3. **Integration Steps**
   - Add to appropriate module (if not standalone)
   - Update routing if needed
   - Add barrel exports for better organization
   - Update index files as necessary

## Command Parameters

- `componentName` - Name of the component (kebab-case)
- `--feature` - Feature module location
- `--service` - Generate corresponding service
- `--routing` - Add routing configuration
- `--skip-tests` - Skip test file generation
- `--standalone` - Force standalone component (override detection)
- `--signals` - Force signal usage (override detection)