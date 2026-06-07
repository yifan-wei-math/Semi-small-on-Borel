# Verifying semi-smallness of the squaring map on the Borel subgroup of GLn(C) for n \leq 5

*This project is not AI-generated. However, the semi-smallness of the squaring map on the Borel subgroup $B$ of $\mathrm{GL}_n$ has been (confidently) conjectured by AI. The raw conversation is recorded here: [https://gemini.google.com/share/74c16ef0f9ae] (warning: lots of misleading arguments and errors). Here is another relevant conversation regarding references: [https://gemini.google.com/share/81166b7922f9]*

Let $f_2 \colon B \to B$ be the squaring map $M \mapsto M^2$, we use the normal form of invertible lower triangular matrices to stratify $B$. Normal form exists for $n \leq 5$, due to finiteness of the number of $B$-orbits on the unipotent radical of $B$.

(Normal forms on $B$ have been constructed in [https://www.numdam.org/item/?id=CM_1987__61_1_3_0]. In fact one should be able to check semi-smallness for $n \leq 7$ based on their results. In their table 2, it can be seen that each orbit of upper triangular matrices contain a matrix with 0, 1 entries. This is what we used to implement the brute-froce search.)

In general the fibers of $f_2$ are easy to analyze. Let $A \in B$ be a matrix on the target, let $M$ be a matrix in the fiber $f_2^{-1}(A)$. The fiber $f_2^{-1}(A)$ is a disjoint union of finitely many $Z_B(A)$-orbits. This is due to the surjectivity of the Lie algebra of $Z_B(A)$ onto the tangent space of $f_2^{-1}(A)$ at every point $M \in f_2^{-1}(A)$. See the following lemma:

**Lemma 1** Let $f_d \colon B \to B$ be the $d$-th power map on $B$. The scheme-theoretic fiber of $f_d$ at any matrix $A$ consists of a finite union of $Z_B(A)$ orbits. 

*The following is an adaptation of an AI generated proof*

**Proof** Let $ad_M$ be the operator on $\mathfrak{b}$ sending $X$ to $XM - MX$. Let $s_{d, M}$ be the operator sending $X$ to $\sum_{i = 0}^{d - 1} M^i X M^{d - 1 - i}$. One has $ad_M$ and $s_{d, M}$ commute, and that $s_{d, M} \circ ad_M = ad_{M^d}$ (this would follow from chain rule applied to $(gMg^{-1})^d$). The tangent space of the fiber of $f_d$ at $M$ is the kernel of $s_{d, M}$. We want to show the natural map $ad_M \colon \mathrm{Ker} ad_{M^d} \to \mathrm{Ker} s_{d, M}$ is surjective. This can be analyzed using commutative algebra. The vector space $\mathfrak{b}$ can be thought of as a finite module on $\mathbb{C}[u, v]$ where $u$ acts as $ad_M$ and $v$ acts as $s_{d, M}$. Since the map $u \colon \mathrm{Ker}(uv) \to \mathrm{Ker}(v)$ is functorial on the category of quasi-coherent sheaves on $\mathbb{C}[u, v]$, we may analyze the map on the support of $\mathfrak{b}$. It's easy to see that as long as $(0, 0)$ does not appear as the support of $\mathfrak{b}$, we will have surjectivity. 

In fact, one can see that $(0, 0)$ does not appear as the support of the larger finite sheaf $\mathfrak{gl}$. On $\mathfrak{gl}$, the Jordan decomposition $M = M_s + M_{nil}$ induces Jordan decompositions for $ad_M = ad_{M_s} + ad_{M_{nil}}$ and $s_{d, M} = s_{d, M_s} + (s_{d, M} - s_{d, M_s})$. Hence it suffices check $(0, 0)$ is not a support in the case when $M = M_s$. On $\mathfrak{gl}$ we may even diagonalize $M_s$, and on each eigenspace the eigenvalue of $ad_{M_s}$ equals $\lambda - \mu$ while the eigenvalue of $s_{d, M_s}$ equals $\frac{\lambda^d - \mu^d}{\lambda - \mu}$, they can't simultaneously be zero since $M_s$ does not have 0 as an eigenvalue.

Therefore, the Lie algebra of $Z_B(A)$ surjects onto the tangent space of the fiber of $f_d$ at every point $M$. *QED*

The above lemma shows the component containing $M$ will have dimension $dim Z_B(A) - dim Z_B(M)$. To verify semi-smallness, it suffices to know how to compute the dimension of each stratum for a nice stratification of the target $B$. This is where the normal form on $B$ comes into play. See the .ipynb file for the rest of the detail on the implementation.
