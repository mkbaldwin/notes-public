# ng-content

Template: 
```html
<div>
    <!-- Some Wrapping HTML -->
    <ng-content></ng-content>
</div>
```

Use:
```html
<my-component>
    <!-- Content -->
</my-component>
```

Can also have multiple content blocks:
```html
<my-component>
    <ng-container someName>
        <!-- Content -->
    </ng-container>
    <ng-container anotherName>
        <!-- Content -->
    </ng-container>
</my-component>
```

Template
```html
<ng-content select="[someName]"></ng-content>
<ng-content select="[anotherName]"></ng-content>
```

Can also use full attribute match in the select portion.