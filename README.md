# optimizer-SUG-torch
Adaptive stochastic gradient method based on the universal gradient method. 
The universal method adjusts Lipsitz constant of the gradient on each step so that the loss function is majorated by the quadratic function. 

###**Adaptive Stochastic Gradient Method (Spokoiny's practical variant)**


---

$\textbf{Input}$: lower estimate for the variance of the gradient $D_0 \le D$, accuracy $0 <                        
\epsilon< \frac{D_0}{L}$, starting point $x_0 \in Q$, initial guess $L_{-1} > 0$


---

 $\textbf{for }${$k=0,1,...$}
 
$~~~~~~~~~~~~$Set $i_k=0$. Set $r^k = \lceil \frac{2 D_0}{L_{k-1}} {\varepsilon}\rceil$, generate i.i.d. $\xi^i_K, ~i = 1,\dots, r^k$
	    
$~~~~~~~~~~~~$$\textbf{repeat }$

$~~~~~~~~~~~~~~~~~~~~$Set $L_k = 2 ^{i_k-1}L_{k-1}$
		
$~~~~~~~~~~~~~~~~~~~~$Calculate $\tilde{g}(x_k) = \frac{1}{r^k}\sum_{i=1}^{r^k}\nabla f(x_k, \xi^i_k)$.
		
$~~~~~~~~~~~~~~~~~~~~$Calculate $w_k = x_k - \frac{1}{2 L_k}\tilde{g}(x_k)$.
		
$~~~~~~~~~~~~~~~~~~~~$Calculate $\tilde{f}(x_k) = \frac{1}{r_k}\sum_{i=1}^{r^k}f(x_k, \xi^i_k)$ and   $\tilde{f}(w_k) = \frac{1}{r^k}\sum_{i=1}^{r^k}f(w_k, \xi^i_k)$.
		
$~~~~~~~~~~~~~~~~~~~~$Set $i_k = i_k + 1$.

$~~~~~~~~~~~~$$\textbf{until }$ $~~~~\tilde{f}(w_k) \le \tilde{f}(x_k) + \langle\tilde{g}(x_k), w_k - x_k\rangle + \frac{2 L_k}{2}\|w_k - x_k\|_2^2 + \frac{\epsilon}{10}$.
		
$~~~~~~~~~~~~$Set $x_{k+1} = w_k,~k=k+1$.
	
$\textbf{endfor}$



---
