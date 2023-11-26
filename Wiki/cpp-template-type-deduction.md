When you template a function in C++, the compiler deduces a type for `T` as well as the `ParamType` in the following pseudocode:

```C++
template<typename T>
void f(ParamType p);
...
f(expr);
```

`ParamType` is usually `T` with some additional qualifiers (`const`, `&`, ...).

Three cases:
# `ParamType` is pointer or reference, but not a [[universal-reference]]
In this case, we ignore the reference-ness of `expr`. Then, we insert expr's type into `ParamType` and deduce `T`. Note that this preserves things like `const`-ness because thats what callers expect.

Note this example
```C++
template<typename T>
void f(const T& param);

int x;
const int cx;
const int& rx;

f(x);  // T = int, param type= const int&
f(cx); // T = int, param type= const int&
f(rx); // T = int, param type= const int&
```
that lets us extract the constness from `T`.
Things work much the same for pointers.

# `ParamType` is a [[universal-reference]]
If `expr` is an *lvalue*, both `T` and `ParamType` are deduced to lvalue references. If it is an *rvalue*, the normal (case 1) rules apply.

```c++
void f(T&& param);

f(x); // x is lvalue => T=int&, paramtype=int&
f(26); // 26 is rvalue => T=int, paramtype=int&&
```

This is the only case where type deduction depends on the rvalue-ness of the arguments. It is also the only time `T` is deduced to be a reference.

Note that even though `ParamType` was declared using rvalue reference syntax, it is deduced to be an lvalue reference in the `f(x)` case.
# `ParamType` is neither pointer nor reference
In this case we are dealing with [[pass-by-value]]. The parameter will be a *copy* of the argument - a totally new object. Accordingly, the rule is that we ignore the reference-ness *and* `const`-ness of `expr` .