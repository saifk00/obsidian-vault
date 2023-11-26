The most pervasive feature of C++11 is move semantics, which is based on the concepts of rvalues and lvalues.
- rvalues: eligible for move operations
- lvalues: 'generally' dont
- heuristic: if you can take its address, its probably an lvalue. otherwise its probably an rvalue
- the *type* of an expression is _independent_ of whether it is an lvalue or rvalue
	- For a type `T`, you may have an lvalue of type `T` or an rvalue of type `T`
```c++
class Widget {
public:
	Widget(Widget&& rhs); // rhs is an lvalue
						  // the type T of rhs is [rvalue reference]
}
```
- Applying the heuristic: we can take the address of `rhs`, so its an lvalue. In fact, *all parameters are lvalues*.
- Any object that is initialized using another object of the same type is called a *copy*, even if it used the move constructor. *rvalue* copies are typically move-constructed.
- If you only know that an object is a copy, you cannot tell how expensive it was to construct. That is because you don't know whether it was move or copy constructed.
- *arguments* may or may not be *lvalues*
	- [[perfect-forwarding]] can pass a parameter to another function while preserving the rvalueness of the original argument