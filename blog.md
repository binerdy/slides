# Adding Fine-Grained Reactivity to Angular with Signals

## Angular's Vision


## Introduction to Signal
The term Signal originates from the functional reactive programming paradigm. A signal can be described as a value that changes over time.

Angular uses the following terminology for signals.

| Function name | Type              | Description |
|---------------|-------------------|-------------|
| signal        | SettableSignal<T> | Producer    |
| computed      | Signal<T>         | Both        |
| effect        | Signal<T>         | Consumer    |

## Signal vs RxJs
Angular uses RxJs to expose streams of events. These streams don't care what the current value is. They are interested in the most recent event.

A RxJs BehaviourSubject is the closest thing the library offers to a signal. It always has a current value. It can notify subscribers of changes to that value, and it exposes a way to get the current value and set a new one. However it is not integrated into RxJs very well. As soon as you use a Pipe it becomes an Observable and it looses the connection that it once was a BehaviourSubject that always has a current value.

For me this information is enough to understand why the Angular team decided to go with something that is exactly what they need instead of bending rxjs into it...
