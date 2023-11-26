In C++, the rules for deducing the type of `auto` is directly related to [[cpp-template-type-deduction]]. There is an algorithm that transforms one to the other.

`auto` => `T`
type specifier for a variable => `ParamType`

example:
```c++
const auto cx  // T = auto, ParamType = const auto
const auto& rx // T = auto, ParamType = const auto&
```

The one exception is for initializer lists:
```C++
auto x3 = {27};
auto x4{27};
```
in both cases, the variables type is `std::initializer_list<int>`.

> You might wonder why auto type deduction has a special rule for braced initializers, but template type deduction does not. I wonder this myself. Alas, I have not been able to find a convincing explanation
> [[meyers-2015]]

