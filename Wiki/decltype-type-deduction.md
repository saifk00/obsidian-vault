Usually, `decltype` just gives you the declared type of a variable without deduction. It is typically used for declaring function templates whose return type depends on multiple parameter types:
```c++
template<typename Container, typename Index>
auto authAndAccess(Container& c, Index i) -> decltype(c[i])
{
	authenticate();
	return c[i];
}
```
It lets us put in some expression of the input parameters and determine the correct output type. To use parameters, you need to put the decltype after the function name using the *trailing return type* syntax.

In C++14 you can do this:
```C++
template<typename Container, typename Index>
auto authAndAccess(Container& c, Index i)
{
	authenticate();
	return c[i];
}
```
But theres a problem - [[auto-type-deduction]] uses [[cpp-template-type-deduction]] rules here - throwing away the reference-ness of the return type. if `c[i]` is a reference type, this will result in a copy! Instead, you can use `decltype(auto)`:

```c++
template<typename Container, typename Index>
decltype(auto) authAndAccess(Container& c, Index i) -> decltype(c[i])
{
	authenticate();
	return c[i];
}
```

Basically, `decltype(auto)` means deduce the type, but using `decltype` rules.