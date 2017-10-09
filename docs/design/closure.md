Closure of Operations

> Where it fits, define an operation whose return type is the same as the type of its arguments
> If the implementer has state that is used in the computation, the the implementer is effectively
> an argument of the operation, so the arguments and return value should be of the same type
> as the implementer.  Such an operation is closed under the set of instances of that type.  A
> closed operation provides a high-level interface without introducing any dependency on other
> concepts

> For the most part, this is an opportunity to look for in VALUE OBJECTS

[Evans, Chapter 10][2003.BlueBook]

```
Probability CombinedWith(Probability)
Probability InverseOf()
Probability Either(Probability)
```
[Greg Young, 2011][2011.ProbabilityKata]

[Monoids, semigroups, and friends][20171005.Seemann]

Taken in the large, this is approximately what we are doing when we are applying commands to aggregates.
Because DDD has its roots in Java, we tend to think in terms of command methods on objects

```
book.buy(...)
```

But that's really just a synonym for
```
Book::buy(mutableReference<Book.State> self, ...)
```
which is to say

```
Book::buy(MutableReference<Book.State> self, ...) {
    Book.State asIs = self.get()
    Book.State toBe = Book::buy(asIs, ...)
    self.replace(asIs, toBe)
}    
```


[2011.ProbabilityKata]: https://gist.github.com/gregoryyoung/1018570
[2003.BlueBook]: http://a.co/22X2xms
[20171005.Seemann]: http://blog.ploeh.dk/2017/10/05/monoids-semigroups-and-friends/