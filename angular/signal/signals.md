---
marp: true
theme: gaia
paginate: true
style: |
  section::after {
    content: attr(data-marpit-pagination) ' / ' attr(data-marpit-pagination-total);
  }
_class:
  - lead
  - invert
---

# Angular Signal

---
## Questions

- Why does Angular need Signal?
- Why not just use RxJs?
- How does Signal's change detection work?
- How is Signal initialized?
- How to update DOM without zone.js and ngZone?

---
## Why Angular needs Signal
Fine-Grained Reactivity in Angular.

Angular uses zone.js to **trigger** global top-down change detection for the whole application.

- Add built-in reactivity using Signal
- Track which parts of the data model components depend on
- Synchronize the UI when that model changes

Source: https://github.com/angular/angular/discussions/49090

---
## Benefits

- Fully zoneless applications
- Simplification of many framework concepts
- Significantly improved interoperability with RxJs

Source: https://github.com/angular/angular/discussions/49090

---
![bg contain](src/change_detection_comparison_01.svg)

---
![bg contain](src/change_detection_comparison_02.svg)

---
![bg contain](src/change_detection_comparison_03.svg)

---
![bg contain](src/change_detection_comparison_04.svg)

---
## Signal vs RxJs

RxJs

- Declare how streams of asynchronous data are handled
- Asynchronous
- Is not glitch free (intermediate state)
- Push changes directly to subscribers

---
## Signal vs RxJs

Signal

- Notify dependend models of changes
- Synchronous
- Is glitch free (no intermediate state)
- Push changes to dependend models
- Dependend models pull changes

---
## Signal vs RxJs
![bg contain](src/diamond_problem.svg)

---
## Signal
* A value that changes over time

Angular terminology

| Function name | Type              | Description |
|---------------|-------------------|-------------|
| signal        | SettableSignal<T> | Producer    |
| computed      | Signal<T>         | Both        |
| effect        | Effect            | Consumer    |

---
## Signal
![bg contain](src/signal_idea.svg)

---
```typescript
@Component({
  selector: 'app-root',
  template: `
    <p>{{ title() }}</p>
    <p>{{ description() }}</p>
  `,
})
export class AppComponent {
  title = signal("angular-example");
  description = computed(() => `The title is ${this.title()}.`);

  constructor() {
    effect(() => console.log(this.description()));
  }
}
```

---
![bg contain](src/signals_timeline_01.svg)

---
![bg contain](src/signals_timeline_02.svg)

---
![bg contain](src/signals_timeline_03.svg)

---
![bg contain](src/signals_timeline_04.svg)

---
![bg contain](src/signals_timeline_05.svg)

---
![bg contain](src/signals_timeline_06.svg)

---
![bg contain](src/signals_timeline_07.svg)

---
![bg contain](src/signals_timeline_08.svg)

---
![bg contain](src/signals_timeline_09.svg)

---
![bg contain](src/signals_timeline_10.svg)

---
![bg contain](src/signals_timeline_11.svg)

---
![bg contain](src/signals_timeline_12.svg)

---
## How to update DOM without zone.js and ngZone


---
![bg contain](src/change_detection_rendering_cycle.webp)