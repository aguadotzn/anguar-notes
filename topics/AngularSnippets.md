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

<details> 
  <summary>Small and useful snippets</summary>
  
  - Route params subscribe
```typescript
this.route.paramMap
  .pipe(map(params => params.get('id')), tap(id => (this.id = +id)))
  .subscribe(id => {});
```
</details>

<!-- NgRx -->
<details> 
  <summary>Ngrx (State Management)</summary>

[NgRx](https://ngrx.io/) is the implementation of the Rx flux pattern. Is the most common state management library in Angular.

- Create an action

```typescript
export const action = createAction('[Source] Event', props<{ key: type }>());
```

- Create an effect

```typescript
effectName$ = createEffect(() => {
  return this.actions$.pipe(
    ofType(action),
    /** An EMPTY observable only emits completion. Replace with your own observable stream */
    operator(() => EMPTY)
  );
});
```

- Create an effect (API CALL)

```typescript
effectName$ = createEffect(() => {
  return this.actions$.pipe(
    ofType(FeatureActions.action),
    operator(() =>
      apiSource.pipe(
        map((data) => FeatureActions.actionSuccess({ data })),
        catchError((error) => of(FeatureActions.actionFailure({ error })))
      )
    )
  );
});
```

- Reducer

```typescript
const featureReducer = createReducer(
  initialState,
  on(featureActions.action, (state) => ({ ...state, prop: updatedValue }))
);
export function reducer(state: State | undefined, action: Action) {
  return featureReducer(state, action);
}
```

- Selector

```typescript
export const selectFeatureProperty = createSelector(
  selectFeature,
  (state: FeatureState, props) => selectLogic
);
```

- Debugging trick: To help you debug you can add this piece of code to your effects:

```typescript
// Debugging purposes only
init$ = createEffect(
  () =>
    this.actions$.pipe(
      ofType(XX),
      tap((action) => console.log('[YY State] Debugging effects', action))
    ),
  { dispatch: false }
);
```

</details>
