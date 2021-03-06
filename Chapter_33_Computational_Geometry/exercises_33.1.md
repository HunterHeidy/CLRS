## 33.1 Line-segment properties

### 33.1-1

> Prove that if $p\_1 \times p\_2$ is positive, then vector $p\_1$ is clockwise from vector $p\_2$ with respect to the origin $(0, 0)$ and that if this cross product is negative, then $p\_1$ is counterclockwise from $p\_2$.

$\dots$

### 33.1-2

> Professor van Pelt proposes that only the $x$-dimension needs to be tested in line 1 of ON-SEGMENT. Show why the professor is wrong.

$(0, 0), (5, 5), (10, 0)$.

### 33.1-3

> The __*polar angle*__ of a point $p\_1$ with respect to an origin point $p\_0$ is the angle of the vector $p\_1 - p\_0$ in the usual polar coordinate system. For example, the polar angle of $(3, 5)$ with respect to $(2, 4)$ is the angle of the vector $(1, 1)$, which is $45$ degrees or $\pi / 4$ radians. The polar angle of $(3, 3)$ with respect to $(2, 4)$ is the angle of the vector $(1, 1)$, which is $315$ degrees or $7\pi / 4$ radians. Write pseudocode to sort a sequence $\langle p\_1, p\_2, \dots, p\_n \rangle$ of $n$ points according to their polar angles with respect to a given origin point $p\_0$. Your procedure should take $O(n \lg n)$ time and use cross products to compare angles.

```python
import math


def sort_by_polar_angle(p0, p):
    a = []
    for i in xrange(len(p)):
        a.append(math.atan2(p[i][1] - p0[1], p[i][0] - p0[0]))
    a = map(lambda x: x % (math.pi * 2), a)
    p = sorted(zip(a, p))
    return map(lambda x: x[1], p)
```


### 33.1-4

> Show how to determine in $O(n^2 \lg n)$ time whether any three points in a set of $n$ points are colinear.

Based on exercise 33.1-3, for each point $p\_i$, let $p\_i$ be $p\_0$ and sort other points according to their polar angles mod $\pi$. Then scan linearly to see whether two points have the same polar angle. $O(n \cdot n \lg n) = O(n^2 \lg n)$.

### 33.1-5

> A __*polygon*__ is a piecewise-linear, closed curve in the plane. That is, it is a curve ending on itself that is formed by a sequence of straight-line segments, called the __*sides*__ of the polygon. A point joining two consecutive sides is a __*vertex*__ of the polygon. If the polygon is __*simple*__, as we shall generally assume, it does not cross itself. The set of points in the plane enclosed by a simple polygon forms the __*interior*__ of the polygon, the set of points on the polygon itself forms its __*boundary*__, and the set of points surrounding the polygon forms its __*exterior*__. A simple polygon is convex if, given any two points on its boundary or in its interior, all points on the line segment drawn between them are contained in the polygon's boundary or interior. A vertex of a convex polygon cannot be expressed as a convex combination of any two distinct points on the boundary or in the interior of the polygon.

> Professor Amundsen proposes the following method to determine whether a sequence $\langle p\_1, p\_2, \dots, p\_{n-1} \rangle$ of $n$ points forms the consecutive vertices of a convex polygon. Output "yes" if the set $\\{ \angle p\_i p\_{i+1} p\_{i+2}: i = 0, 1, \dots, n - 1 \\}$, where subscript addition is performed modulo $n$, does not contain both left turns and right turns; otherwise, output "no." Show that although this method runs in linear time, it does not always produce the correct answer. Modify the professor's method so that it always produces the correct answer in linear time.

A line.

### 33.1-6

> Given a point $p\_0 = (x\_0, y\_0)$, the __*right horizontal ray*__ from $p\_0$ is the set of points $\\{ p\_i = (x\_i, y\_i) : x\_i \ge x\_0 \~\text{and}\~ y\_i = y\_0 \\}$, that is, it is the set of points due right of $p\_0$ along with $p\_0$ itself. Show how to determine whether a given right horizontal ray from $p\_0$ intersects a line segment $\overline{p\_1 p\_2}$ in $O(1)$ time by reducing the problem to that of determining whether two line segments intersect.

$p\_1.y = p\_2.y = 0$ and $\max(p\_1.x, p\_2.x) \ge 0$.

or

$\text{sign}(p\_1.y) \ne \text{sign}(p\_2.y)$ and $\displaystyle p\_1.y \cdot \frac{p\_1.x - p\_2.x}{p\_1.y - p\_2.y} \ge 0$

### 33.1-7

> One way to determine whether a point $p\_0$ is in the interior of a simple, but not necessarily convex, polygon $P$ is to look at any ray from $p\_0$ and check that the ray intersects the boundary of $P$ an odd number of times but that $p\_0$ itself is not on the boundary of $P$. Show how to compute in $\Theta(n)$ time whether a point $p\_0$ is in the interior of an $n$-vertex polygon $P$. (Hint: Use Exercise 33.1-6. Make sure your algorithm is correct when the ray intersects the polygon boundary at a vertex and when the ray overlaps a side of the polygon.)

Based on exercise 33.1-6, use $p\_i - p\_0$ as $p\_i$.

### 33.1-8

> Show how to compute the area of an $n$-vertex simple, but not necessarily convex, polygon in $\Theta(n)$ time. (See Exercise 33.1-5 for definitions pertaining to polygons.)

Half of the sum of the cross products of $\{\overline{p\_1 p\_i}, \overline{p\_1 p\_{i+1}} \~|\~ i \in [2, n - 1] \\}$.
