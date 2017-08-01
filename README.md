# Human Protein Atlas co-expression

This notebook was done for the NCATS translator Project


## Goal
Find genes which are co expressed with known genes known to implicate them.

## Process
Given a gene's expression level in a set of tissues (and cell types; now just called tissues)
compare it with all other genes expression levels in the same tissues.  

To compare, find the absolute difference in expression levels between genes across all tissues
and sum the differences.

Since we only have four levels from `None` to `High` we can use `(0,1,2,3)`
and a constant number of tissues (about 100) we can normalize the difference
in expression for each pair of genes (about 85 million pairs in this case).

Taking only perfectly correlated pairs, no (reported) difference in expression,
we end up with under 30 thousand pairs which "cluster" into about 200 connected components.

A cursory glance shows a few components with many genes and many components with few genes
where many and few are relative to the sixty we would expect if they were uniformly distributed.

The clusters also display an affinity for grouping genes with similar gene family nomenclature together 

# Result
Nada, zip, nothing.  
Unfortunately none of the 27 Fanconi genes we are interested are in this set of 13 thousand genes.


# Discussion

Still seems to be a process worth pursuing with other expression data sets.

I do have one concern which is sum of absolute difference is a great leveler.
Weak expression can look just like strong similarity so I should
look into bringing the total expression back into the metric.

Also looking at the variance in expression levels within a cluster
may tell us something about the utility of that clustering,
with low variance being more believable than high variance.
