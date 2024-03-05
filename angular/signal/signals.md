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

# Angular Signals

---
## Content

- What are Angular Signals?
- Demo
- How are Signals initialized?
- Why does Angular want Signals?
- Why doesn't Angular just use RxJs?

---
![bg contain](src/signals_1.png)

---
![bg contain](src/signals_2.png)

---
![bg contain](src/signals_3.png)

---
![bg contain](src/signals_4.png)

---
![bg contain](src/signals_5.png)

---
![bg contain](src/signals_6.png)

---
![bg contain](src/signals_7.png)

---
![bg contain](src/signals_8.png)

---
![bg contain](src/signals_9.png)

---
![bg contain](src/signals_10.png)

---
![bg contain](src/signals_11.png)

---
![bg contain](src/signals_12.png)

---
## Demo

---
![bg contain](src/signals_timeline_00.svg)

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
## Why does Angular want Signals?

Because of their high level goals.
- Fine-Grained Reactivity in Angular
- Path towards zoneless applications
- Simplification of framework concepts
- Interoperability with RxJs

Source: [RFC](https://github.com/angular/angular/discussions/49685)

---
## Fine-Grained Reactivity
- Comparison zone.js vs Signals

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

- Declare how streams of asynchronous data is handled
- Asynchronous
- Is not glitch free (intermediate state)
- Push changes directly to subscribers

---
## Signal vs RxJs

Signal

- Notify dependencies of changes
- Synchronous
- Is glitch free (no intermediate state)
- Push changes to dependencies
- Dependencies pull changes

---
## RxJs
![bg contain](src/diamond_problem.svg)

---
## Signal
![bg contain](src/no_diamond_problem.svg)
