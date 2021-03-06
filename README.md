# Rx Lite
Rx Lite - my own implementation of some methods from Rx library just for educational purpose.

## Samples

```javascript
Rx.Observable.from([1, 2, 3, 4])
    .map(value => value * 10)
    .map(value => value + 1)
    .find(value => value > 25)
    .subscribe(val => console.log(val), (error) => {}, () => console.log('completed'));
```

```javascript
Rx.Observable.fromRange(1, 20)
    .map(val => val + 1)
    .filter(val => val % 2 == 0)
    .do(val => console.log(val))
    .take(5)
    .reduce((val, sum) => sum + val, 0)
    .subscribe(val => console.log(val), (error) => {}, () => console.log('completed'));
```

```javascript
Rx.Observable.from([1, 2, 3, 4])
    .concat(Rx.Observable.from([10, 20, 30, 40]), Rx.Observable.from([100, 200, 300, 400]))
    .subscribe(Rx.Observer.create(val => console.log(val), (error) => {}, () => console.log('completed')));
```

```javascript
Rx.Observable.fromRange(1, 3)
    .flatMap(function (x) {
      return Rx.Observable.fromRange(x, x + 1);
    })
    .subscribe(val => console.log(val), (error) => {}, () => console.log('completed'));
```

```javascript
Rx.Observable.interval(1000)
    .take(3)
    .merge(Rx.Observable.interval(1100).take(2))
    .map(() => 'tick')
    .subscribe(val => console.log(val), (error) => {}, () => console.log('completed'));
```

```javascript
var source = Rx.Observable.interval(1000)
    .take(2)
    .do(() => console.log('Side effect'))
    .publish();

source.subscribe(val => console.log('publish1 tick'));
source.subscribe(val => console.log('publish2 tick'));
```

```javascript
Rx.Observable.fromEvent(document.getElementById('clickme'), 'click')
    .takeUntil(Rx.Observable.interval(4000))
    .subscribe(val => console.log('clicked 1'), (error) => {}, () => console.log('completed'));
```

## Resources

### Reactive programming
 * [Rx Book](https://xgrommx.github.io/rx-book/)
 * [The introduction to Reactive Programming you've been missing](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)
 * [Learning Observable By Building Observable](https://medium.com/@benlesh/learning-observable-by-building-observable-d5da57405d87)
 * [Hot vs Cold Observables](https://medium.com/@benlesh/hot-vs-cold-observables-f8094ed53339)

## Functional Programming
 * [ESLint for functional programming](https://github.com/dustinspecker/awesome-eslint)

### ES6
 * [ECMAScript 6 modules: the final syntax](http://www.2ality.com/2014/09/es6-modules-final.html)
 * [Babel & Webpack](http://www.2ality.com/2015/04/webpack-es6.html)
