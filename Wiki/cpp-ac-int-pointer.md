https://godbolt.org/z/YGzr87TvT

explanation

actually all thats needed in this case is to mark the `my_type(T2 p)` constructor `explicit`.. if you switch the compiler to gcc youll see this slightly more helpful error

```
source>: In function 'int main()': <source>:56:13: warning: ISO C++ says that these are ambiguous, even though the worst conversion for the first is better than the worst conversion for the second:    56 |     *(ptr + 4) = 2;       |             ^ <source>:14:12: note: candidate 1: 'my_ptr<T> my_ptr<T>::operator+(diff_type) const [with T = my_type<float>; diff_type = long int]'    14 |     my_ptr operator+(diff_type r) const {       |            ^~~~~~~~ <source>:46:27: note: candidate 2: 'constexpr RT operator+(const my_type<T>&, const T2&) [with T2 = int; RT = int; T = float]'    46 |     friend constexpr auto operator+(const my_type<T> &op, const T2 &op2) -> RT {
```

basically the single-arg constructor can be used to implicitly convert `my_ptr<my_type<float>>` into `my_type<float>` and the compiler is forced to consider this option as equally viable