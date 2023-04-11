testing

<details> 
  <summary>Create component</summary>
  
  You can use the CLI. `ng g c nameComponent`
```typescript
  @Component({
    selector: 'selector-name',
    templateUrl: 'name.component.html',
  })
  export class NameComponent implements OnInit {
    constructor() {}
    ngOnInit() {}
}
```
</details>