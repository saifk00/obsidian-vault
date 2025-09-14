## Guiding Questions
- its often said that divergenece represents 'how much stuff appears to come out of this point in space' - i dont get that because sources and sinks are single points in the field - so i would imagine divergence to be a boolean function (yes/no). Why is it a scalar function?
- What is the physical interpretation of vector potentials and how does this relate to the B field? Why do we need this mathematical abstraction?

# Notes

## Section 1 - Vectors

### Vector Triple Product (BAC-CAB Formula)
The vector triple product **A** × (**B** × **C**) has the identity:
**A** × (**B** × **C**) = **B**(**A** · **C**) - **C**(**A** · **B**) = (**A**·**C**)**B** - (**A**·**B**)**C**

**Geometric Intuition:** This result is a vector that lies in the **BC** plane. The reasoning is elegant:
- **B** × **C** is the normal vector to the **BC** plane
- The cross product of any vector **A** with this normal must return to the **BC** plane
- Therefore, **A** × (**B** × **C**) is expressible as a linear combination of **B** and **C**

This geometric understanding makes the BAC-CAB formula intuitive rather than just algebraic manipulation.

### Green's/Gauss Theorem Intuition
Green's theorem (fundamental theorem for line integrals) makes intuitive sense when you realize that any path between two points in a vector field **T** is composed of infinitesimal pieces d**L**.

The change along each piece is given by ∇**T** · d**L**, and summing these up along the entire path is equivalent to simply taking the difference between the starting and ending values:

∮ ∇**T** · d**L** = **T**(b) - **T**(a)

**Analogy:** This is like measuring the height of the CN Tower - you could either:
1. Measure the height of each floor and multiply by the number of floors climbed, or
2. Simply subtract the altimeter reading at the bottom from that at the top

Both approaches give the same result, but the second is much simpler.

### Helmholtz Theorem
The Helmholtz theorem states that the curl and divergence of a vector field, plus boundary conditions, uniquely determine the field. This is intuitive because there's a hidden constraint: the field must be smooth (continuous and differentiable).

The smoothness requirement is crucial - without it, you could have discontinuous "jumps" that wouldn't be captured by local derivatives like curl and divergence. The theorem essentially says that if you know how the field "twists" (curl) and "spreads" (divergence) everywhere, plus what happens at the boundaries, you've completely specified a smooth vector field.
