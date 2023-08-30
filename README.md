# Geogebra-Fractions
A collection of GGB tools to implement the rational numbers data type as two element lists. Also some bidimensional vectors with rational components is implemented. More on defining tools can be found [here](https://primi235711.altervista.org/moodle/course/view.php?id=5#section-4)

To use them take the basic-empty-library.ggb  This file has all the tools and no construction. File empty-library.ggb  has all the tools and some basic construction. The file example-with-library.ggb contains an example for a quiz on the bisector line.

The set of GGB tools are created with the following inputs to the command line in GGB Rationals are represented by two element lists {a,b} is a/b

`qn={1,2}`
`qa={1,2}`
`qb={1,2}`

Simplification qs gives the most simplified fraction with positive denominator

`qsin={Element[qn, 1] / GCD[Element[qn, 1], Element[qn, 2]], Element[qn,2] / GCD[Element[qn, 1], Element[qn, 2]]}`

`qs=If(Element(qsin, 1) > 0, If(Element(qsin, 2) > 0, qsin, {-Element(qsin, 1), -Element(qsin, 2)}), If(Element(qsin, 2) > 0, qsin, {-Element(qsin, 1), -Element(qsin, 2)}))`

multiplication
`qm={Element[qa, 1] Element[qb, 1], Element[qa, 2] Element[qb, 2]}`

plus
`qp={Element[qa, 1] LCM[Element[qa, 2], Element[qb, 2]] / Element[qa, 2] + Element[qb, 1] LCM[Element[qa, 2], Element[qb, 2]] / Element[qb, 2], LCM[Element[qa, 2], Element[qb, 2]]}`

opposite -qa
`qo={-Element[qa, 1], Element[qa, 2]}`

inverse 1/qa
`qi={Element[qa, 2], Element[qa, 1]}`

exponentiation
`qe=If[n>0, {Element[qa, 1]^n, Element[qa, 2]^n},{Element[qa, 2]^n, Element[qa, 1]^n}]`

test equality
`qeq=qs[qa]==qs[qb]`

merge to real
`nq=Element[qa, 1] / Element[qa, 2]`

from integer to exact rational 
`qn={n, 1}`

output as a string qout(num,den) pretty output e.g. -2 
`qout=If(qoutNum qoutDen < 0, "-") If(abs(qoutDen) == 1, Text(abs(qoutNum)), "\frac{" Text(abs(qoutNum)) "}{" Text(abs(qoutDen)) "}")`

output non simplified for a couple qoprt({n,d})
`qoprt=qout(Element(qa, 1), Element(qa, 2))`

output simplified
`qprn=qoprt(qs(qa))`
Each create a single tool that is available here as a .ggt. 

This data type then is used to build a data type for two dimensional vectors
represented as list of TWO lists of TWO integers e.g. {{1, 2}, {3, 4}} for (1/2,3/4). GGB represent this as a matrix but this feature in not used. 

The operations are:
sum 
`vp={qp[Element[va, 1], Element[vb, 1]], qp[Element[va, 2], Element[vb, 2]]}`

opposite
`vo={qo(Element(va, 1)), qo(Element(va, 2))}`
dot product
`vd=qp[qm[Element[va, 1], Element[vb, 1]], qm[Element[va, 2], Element[vb, 2]]]`

scalar product
`vsp={qm[qa, Element[va, 1]], qm[qa, Element[va, 2]]}`

generate a unitary vector with rational components for two m,n naturals 
`pyt={{(m + n)² - n², (m + n)² + n²}, {2 (m + n) n, (m + n)² + n²}}`

slope of a vector with rational components as a rational number
`qslope=qm(Element(va, 2), qi(Element(va, 1)))`

print a vector as a couple
`vprn="\left(" Text(Element(va,1)) "," Text(Element(va,2)) "\right)"`

print a vector as a column
`vcprn="\left(" Text(Element(va,1)) "," Text(Element(va,2)) "\right)"`

a vector with rational components to a GGB std point
`P=(nq(Element(va, 1)), nq(Element(va, 2)))`

a couple of points with rational coordinates into a standard GGB vector.
First parameter is vector starting point.
`V=Vector(P(va), P(vb))`
