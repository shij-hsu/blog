Grover's Algorithm

1. Let |s> denote the unform superposition over all states

$$|s>=\frac{1}{\sqrt{N}}\sum_{x=0}^{N-1}|x>​$$

2. Then the operator $$U_s=2|s><s|-I$$ is known as the Grover diffusion operator
3. Here is the algorithm:
4. Initialize the system to the state 

$$|s>=\frac{1}{\sqrt{N}}\sum_{x=0}^{N-1}|x>$$

5. Perform the following "Grover iteration"

r(N) times, which is asymptotically $$O(N^{1/2})$$,  is described below.

- Apply the operator $$U_\omega$$
- Apply the operator $$U_s$.

6. Perform the measurement $$\Omega$$. The measurement result will be eigenvalue $$\lambda_\omega$$ with probability approaching 1 for N>>1. From *$$\lambda_\omega$$*, $$\omega$$ may be obtained.