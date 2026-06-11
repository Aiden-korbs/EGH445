# Kalman Filter Tuning Strategies

## Choosing R

R \in \mathbb{R}^{p\times p}, where p is the number of outputs.

Often diagonal, when sensor noise is uncorrelated:

$$R_k=\begin{bmatrix}\sigma_{v_1}^2&0&\cdots&0\\0&\sigma_{v_2}^2&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&\sigma_{v_p}^2\end{bmatrix}$$

### Determining Values

- **Sensor datasheets**: specified noise characteristics
- **Experimental data**: calculated variance from samples
- **Cross-correlation**: covariance between sensor signals

## Choosing Q

Q \in \mathbb{R}^{n\times n}, where n is the number of states.

Often diagonal and treated as a tuning parameter:

$$Q_k=\begin{bmatrix}\sigma_{w_1}^2&0&\cdots&0\\0&\sigma_{w_2}^2&\cdots&0\\\vdots&\vdots&\ddots&\vdots\\0&0&\cdots&\sigma_{w_n}^2\end{bmatrix}$$

### Determining Values

- **\sigma_{w_i}^2** reflects how much x_i is expected to deviate
- **Physical insight**: deviation due to real dynamics
- **Iterative tuning**: observe residual e(kT)

## Diagonal Matrices for Uncorrelated Noise

When noise sources are uncorrelated, diagonal matrices are appropriate and simplify tuning significantly — each diagonal element can be adjusted independently.
