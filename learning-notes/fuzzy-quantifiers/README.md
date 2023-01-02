## Fuzzy Quantifiers

Quantified statements such as 

> "Most students pay their own tuition" or "About half the guests gave presents" 

provide a very significant means by which people summarize observations about the world. 

Any attempt to build intelligent computer based systems must provide a mechanism for representing and reasoning with such statements.

Lotfi A. Zadeh suggested an aprroach for the representation and manipulation of quantified statements based upon the use of fuzzy sets.

> **Fuzzy Sets**
> A Fuzzy set is a pair (U,m) where U is a set and $$m: U \rightarrow [0,1]$$ a membership function.
>set U is called universe of discourse, and for each $x \in U$, the value m(x) is called the grade of membership of x in (U,m).
>Let $x \in U$ then x is called: 
>
> **not included** in the Fuzzy set (U,m) if $m(x) = 0$
>
>**fully included** if $m(x) = 1$
>
>**partially included** if $0 < m(x) < 1$ 


- Montague - Contributed to our understanding of proper treatments of quantifiers `all`, `some` and `any`
- Barwise and Cooper - Described methods for dealing with `generalized quantifiers` exemplified by `most`,   `many`.
- Zadeh and Others - Described in a series of papers from 1975. Quantifiers above as well as some other quantifiers w/ imprecise meaning `few`, `several`, `not very many` are treated as **`fuzzy numbers`** and referred to as fuzzy quantifiers.

To illustrate the concept we may think about the quantifier `most` given the sentence "Most big men are nice" what is the degree defines the most? For all we know it could be any number above %51.

It is interpreted as a fuzzily defined proportion of the fuzzy set of kind men in the fuzzy set if big men. Then, the `Cardinality` concept of a fuzzy set is used compute the proportion in question and find the degree to which it is compatible with the meaning of `most`.


```mermaid

graph TD;
  fuzzyquantifiers(Fuzzy Quantifiers);
  fuzzyquantifiersoffirst(First Kind - Absolute);
  fuzzyquantifiersofsecond(Second Kind - Relative);
  fuzzyquantifiersofthird(Third Kind - Ratios);

  ap5[Approxiamately five]
  alf[A Large Fraction]
  fuzzyquantifiers-->fuzzyquantifiersoffirst;
  fuzzyquantifiers-->fuzzyquantifiersofsecond;

  fuzzyquantifiersoffirst-->Several;
  fuzzyquantifiersoffirst-->Few;
  fuzzyquantifiersoffirst-->ap5;
  fuzzyquantifiersoffirst-->Many;

  fuzzyquantifiersofsecond-->Many
  fuzzyquantifiersofsecond-->Most
  fuzzyquantifiersofsecond-->alf
  fuzzyquantifiersofsecond-->Often
  fuzzyquantifiersofsecond-->fuzzyquantifiersofthird

  llr[Likelihood Ratios]
  cf[Cerainty Factors]  
  fuzzyquantifiersofthird-->llr
  fuzzyquantifiersofthird-->cf

```

We are employing the Absolute (first kind) and Relative (second kind) Fuzzy Quantifiers to refer to Absolute and Relative counts. Observe that a quantifier such as `many` could be employed in either sense depending on the context.


- Examples of quantifiers of the first kind are: severul, few, many, not very
many, approximately five, close to ten, much larger than ten, u large number, etc. 
- Examples of second kind are: most, many, a large fruction, often, once in a while, much of, etc. Where needed, ratios of fuzzy quantifiers of the second kind will be referred to as fuzzy quantifiers of the third kind. Examples of quantifiers of this type are the likelihood ratios and certainty factors which are encountered in the analysis of evidence, hypothesis testing and expert systems

Fuzzy Quantifiers in out daily life appear implicitly rather than explicitly, when it is asserted that:
- `"Basketball players are very tall"` it is meant `"Almost all basketball players are very tall"`
- `"Lynne is never late"` it is meant `"Lynne is late very rarely"`.

