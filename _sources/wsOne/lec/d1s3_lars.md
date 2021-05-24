# Multigrid in Hierarchical Low Rank Tensor Formats

- By [Lars Grasedyck](https://www.igpm.rwth-aachen.de/grasedyck)
- RWTH Aachen University
- [Video here](http://www.ipam.ucla.edu/abstract/?tid=16626&pcode=TMWS1)

> In this presentation we give a brief introduction to hierarchial low rank tensor formats for the representation of high-dimensional tensors that fulfil certain rank bounds or singular value decay of corresponding matricizations.

> In order to solve systems of equations in these formats there are already many developed and practically useful methods available. However, their convergence and convergence rates are difficult to analyse. On the other hand multigrid methods are well analysed with superior convergence rates. We use the classical multigrid convergence theory by providing a smoother and prolongations / restrictions that comply with low rank tensor formats. Prolongation and restriction are naturally given in a low rank tensor formulation. The smoother is an approximation of Jacobi based on a truncated exponential sum, thereby adapting it to the low rank format.

## Notes

```{note}
These are essentially a rough sketch of the slides. 
```

For model (and complex) problems the main goal is the ability to have a **convergence guarantee**.

```{admonition} Click to expand ugly scribbled transcript
:class: dropdown
![Slide1](d1s3/wks1p_1.*)
![Slide2](d1s3/wks1p_2.*)
![Slide3](d1s3/wks1p_3.*)
![Slide4](d1s3/wks1p_4.*)
![Slide5](d1s3/wks1p_5.*)
![Slide6](d1s3/wks1p_6.*)
![Slide7](d1s3/wks1p_7.*)
```

### Main results
Detailed in {cite}`grasedyckParameterdependentSmootherMultigrid2020` along with some earlier related results {cite}`grasedyckDistributedHierarchicalSVD2018,grasedyckHierarchicalSingularValue2010`

- HT-approximability for inverse of diagonal matrix
- Convergence proof (uniform) for multigrid (parameter $p$)

### Open Questions
- Other smoothers
- Algebraic Multigrid
- Matrix (parameter $p$) dependent prolongation / restriction
- Dimension $(d)$ reduction on coarse grids

## References

```{bibliography}
:filter: docname in docnames
```
