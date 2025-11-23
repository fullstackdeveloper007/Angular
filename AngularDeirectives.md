# Directives 


Types of Directive
* Component --> @Component({ selector: 'app-user',  templateUrl: './user.component.html'})
* Attribute directives  --> ngClass,ngStyle,ngModel,ngForm
* Structural directive -->*ngIf,*ngFor,*ngSwitch, *ngSwitchCase
* Custome Structural Directive

```
ng g directive directives/highlight-completed-todo
```


### ControlFlow blocks (Angular 17+)
### **1. @if**

```ts
@if (condition) {
   <div>...</div>
}
@for (item of list) {
   <div>{{ item }}</div>
}

```

### **2. @for**
```ts
@for (user of users; track user.id) {
  <div>{{ user.name }}</div>
}
```

### **3. @switch, @case, @default**
  <div [ngSwitch]="role">
  <span *ngSwitchCase="'admin'">Admin</span>
  <span *ngSwitchCase="'user'">User</span>
  <span *ngSwitchDefault>Guest</span>
</div>


