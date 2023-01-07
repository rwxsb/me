# Fuzzy Quantifiers

## A Computational Approach To Fuzzy Quantifiers in Natural Languages

### Introduction
Quantified statements such as 

> "Most students pay their own tuition" or "About half the guests gave presents" 

provide a very significant means by which people summarize observations about the world. 

Any attempt to build intelligent computer based systems must provide a mechanism for representing and reasoning with such statements.

Lotfi A. Zadeh suggested an aprroach for the representation and manipulation of quantified statements based upon the use of fuzzy sets.

> **Fuzzy Sets**
> A Fuzzy set is a pair (U,m) where U is a set and $$\mu: U \rightarrow [0,1]$$ a membership function.
>set U is called universe of discourse, and for each $x \in U$, the value $\mu(x)$ is called the grade of membership of x in (U,$\mu$).
>Let $x \in U$ then x is called: 
>
> **not included** in the Fuzzy set (U,$\mu$) if $\mu(x) = 0$
>
>**fully included** if $\mu(x) = 1$
>
>**partially included** if $0 < \mu(x) < 1$ 


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

An interesting note about the fuzzy quantifiers should be made regarding the transitive closure.
$p \equiv  all A's\ are\ B's$ and $q \equiv  all B's\ are\ C's$ then
$r \equiv  all A's\ are\ C's$ the quantifier `all` in p and q is replace by `almost all`, then the quantifier all in r should be replace by `none-to-all`. Slight change in quantifiers in premises may result in conclusion.

Natural way to dealing with the fuzzy quantifiers is to treat them as fuzzy numbers. However this does not mean that the fuzzy quantifiers exist together with fuzzy number.

In the proposition “Vickie is several years younger than Mary.” `several` - fuzzy number does not play the role of a fuzzy quantifier whereas in "Vickie has several good friends." it does.

“Vickie has several credit cards,” several is a fuzzy characterization of the cardinality of the nonfuzzy set of Vickie’s credit cards; in “Vickie has
several good friends,” several is a fuzzy characterization of the cardinality of the fuzzy set of Vickie’s good friends;

A Simple example to show how Fuzzy Quantifiers can be treated as Fuzzy numbers

$$ p \equiv  80\% of students\ are\ single$$ 
$$q \equiv  60\% of students\ are\ male$$ 
$$r \equiv  Q\ of\ students\ are\ single\ and\ male$$ 

$r$ is the answer to the question "What percentage of students are sinle and male?" Clearly the answer is $80\%x60\%=48\%$ 

We may generalise this in $p \equiv  Q_1\ of\ A's\ are\ B's$ and $q \equiv  Q_2\ of\ (A\ and\ B)'s\ are\ C's$ then $r \equiv  Q_1Q_2\ of\ A's are (B\ and\ C)'s$

Assume $Q_1$ and $Q_2$ are fuzzy quantifiers of second kind - Relative
$$ p \equiv  most\ of students\ are\ single$$ 
$$q \equiv  a\ little\ more\ than\ a\ half\ of students\ are\ male$$ 
$$r \equiv  ?Q\ of\ students\ are\ single\ and\ male$$ 

where the question mark indicates that value of Q to be inferred from $p$ and $q$.

Interpreting most, a little more than a half and Q as fuzzy numbers we can see that Q may be expressed as a product in fuzzy arithmetic $Q = most \otimes a\ little\ more\ than\ a\ half$

>**Intersection/Product Syllogism**
>
>We may generalise this in $p \equiv  Q_1\ of\ A's\ are\ B's$ and $q \equiv  Q_2\ of\ (A\ and\ B)'s\ are\ C's$ then $r \equiv  Q_1 \otimes Q_2\ of\ A's are (B\ and\ C)'s$

![Intersection/Product Syllogism](intersection-product-syll.png)

We assumed that Fuzzy Quantifier is a `fuzzy number of type 1`

### Cardinality of Fuzzy Sets

In case of crisp (nonfuzzy) subset, A of a universe discourse, U, the proposition "u is an element of A" is either true or false.

In the case of fuzzy subset, F, of U, the proposition "u is an element of F" is generally true to degree, with result of cardinality admitting to multiple definitions. 
- Associate with F a real number then result of cardinality is nonfuzzy
- Associate with F a fuzzy number since it is argued cardinality of fuzzy set should be a fuzzy number

In a Finite Universe a fuzzy subset F, of $U = {u_1, ... , u_n}$ may be expressed symbolically as 
$$ F = \mu_1u_1 + ... + \mu_nu_n $$
where for $\mu_iu_i$ $i = 1,..,n$ and $\mu_i$ is the grade of membership of $u_i$ in F and plus sign is union.

#### Nonfuzzy cardinality
We may simply extend the concept of cardinality by forming the `sigma count`.

>**Sigma Count**
>
>$$ \sum Count(F) \equiv \sum_i \mu_i$$ 
>where $i = 1...n$
>
> We may put a certain threshold to exlude the members whos grades membership falls below. The purpose of such an exclusion is to
avoid a situation in which a large number of terms with low grades of membership become count-equivalent to a small number of terms with high membership.

We may illustrate the concept of sigma count with below example, Assume that the fuzzy set of close friends of Teressa is expressed as 

$$ F = 1Enrique + 0.8 Ramon + 0.7 Elie + 0.9 Sergei + 0.8 Ron$$
In this case $\sum Count(F) = 1 + 0.8 + 0.7 +0.9 + 0.8 = 4.2$

>**Weighted Sigma Count**
>
>Sigma count could be weighted, in the sense that if $w = (w_1,...,w_n)$ is an n-tuple of non-negative real numbers, then below is called the weighted sigma count of F wrt w
>$$\sum Count(F;w) \equiv \sum_iw_i\mu_i$$
>where $i = 1...n$
>
>This definition implies that $\sum Count(F;w)$ may be interpreted as the sigma-count of a fuzzy
multiset ‘F in which the grade of membership and the multiplicity of $u_i, i = 1,. . . n$ are,
respectively, $\mu_i\ and\ w_i$

Above definitions hold for the assumption that cardinality of a fuzzy set is a real number

#### Fuzzy Cardinality
If we assume that cardinality of a fuzzy set is a fuzzy number we may begin our discussion by representing F with its level sets

$$ F = \sum_\alpha  \alpha F_\alpha $$

in which $\alpha-level-sets$ $F_\alpha$ are non-fuzzy sets defined by

$$ F_\alpha = \{u | \mu_F(u) \geq \alpha \}\ where\ 1 \geq \alpha > 0$$

Based on this assumption there are three FCounts:
- FGCount
- FLCount
- FECount

We may define the above counts using the membership function $\mu$ of a Fuzzy set $let\ i = 0,1,...,n$ then:

>**FGCount(F)**
>
>$$\mu_{FGCount(F)}(i) \equiv \sup_{\alpha} \{\alpha | Count(F_\alpha) \geq i \} $$

>**FLCount(F)**
>
>$$\mu_{FLCount(F)}(i) \equiv \sup_{\alpha} \{\alpha | Count(F_\alpha) \geq n - i \} $$

>**FECount(F)**
>
>$$\mu_{FECount(F)}(i) \equiv Min(\mu_{FLCount(F)}(i) , \mu_{FLCount(F)}(i)) $$

Consider the example:
Let $F = 0.6u_1 + 0.9u_2 + 1u_3 + 0.7u_4 + 0.3u_5$ by the definition of $F_\alpha$ we may say that 

$$ F = 1(u_3) + 0.9(u_2 + u_3) + 0.7(u_2 + u_3 + u_4) + 0.6(u_1 + u_2 + u_3 + u_4) + 0.3(u_1 + u_2 + u_3 + u_4 + u_5)$$

so we have 

$$ FG Count(F) = 1|0 + 1|1 + 0.9|2 + 0.7|3 + 0.6|4 + 0.3|5 $$
$$ FL Count(F) = 0.1|2 + 0.3|3 + 0.4 | 4 + 0.7|5 + 1|6 + ... \Theta 1 \\ = 0.1|1 + ...$$
$$ FE Count(F) = 0.1|1 + 0.3|2 + 0.4|3 + 0.6|4 + 0.3|5 $$

where $\sum Count(F) = 0.6 + 0.9 + 1.0 + 0.7 + 0.3 = 3.5$


#### Relative count
A type of count that plays important role in representation of realtive count (or relative cardinality) is relative sigma count

>**Relative Sigma Count**
>
>$$\sum Count(F/G) = \frac{\sum Count(F \cap G)}{\sum Count(G)}$$
> represents the proportion of elements of F which are in G

>**$ F \cap G$**
>
>$$ \mu_{F \cap G}(u) = \mu_F(u) \land \mu_G(u)$$

Observe that $\sum Count(F/G) = Prop(G/F)$

## Reasoning with Fuzzy Quantified Statements

>**Definition**
>
>A linguistic (fuzzy) quantifier of the first kind is a value such as "about 5", "at least one", "more than 10" indicating the absolute quantity can be represented as a fuzzy subset of $Q_1$ or non-negative real numbers, r, $Q_1(r)$ measures the deree to which r satisfies the concept of $Q_1$

>**Definition**
>
>A linguistic (or fuzzy) quantifier of second kind is a value such as, "almost all", "about 50%", "nearly a third" indicating a relative or proportional quantity. A quantifier of the second kind can be represented as a fuzzy subset $Q_2$ of the unit internal I, such that for each $r \in T, Q_2(r)$ measures the degree to which r satisfies the concept of $Q_2$

Linquistic quantifiers appear often in natural language statements. We have below the three prototypical usages

(1) "There are about seven tall people" is an example of the quantified statement of the form
$$There\ are\ Q_1\ T's$$
where $Q_1$ - _about seven_ - is a kind one quantifier and $T$ - _tall_ - fuzzy subset of elements. 



#### Validating Quantified statements from given sets

There are various types of problems dealing with quantifiers in this section we will deal with the first type.

Given a fuzzy set of elements A and we desire to find the truth about some quantified statement about A.

Given the heights of a group of people and we are asked how true is the statement "Most people of this group are tall?"

In such class of problems given fuzzy subsets act as our database of knowledge, from which we are interested in inferring the validity of some proposition. Assume that A and B are known fuzzy subsets of X, and consider statement There are $Q_1\ A's$











