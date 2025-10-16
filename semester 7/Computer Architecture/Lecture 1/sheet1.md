
 # Example @ 34

 Assume a disk subsystem with the following components and MTTF:
 * 10 disks, each rated at 1,000,000-hour MTTF
 * 1 ATA controller, 500,000-hour MTTF
 * 1 power supply, 200,000-hour MTTF
 * 1 fan, 200,000-hour MTTF
 * 1 ATA cable, 1,000,000-hour MTTF

 Using the simplifying assumptions that the lifetimes are exponentially distributed
 and that failures are independent, compute the MTTF of the system as a whole.

### Answer
The Mean Time To Failure (MTTF) for the system is calculated as the reciprocal of the total system failure rate:

$$
\text{MTTF}_{\text{ System}} = \frac{1}{\text{Failure rate of the system}}
$$
$$
\text{Failure rate}_{\text{ System}} = 10 \times \frac{1}{1,000,000} + \frac{1}{500,000} + \frac{1}{200,000} + \frac{1}{200,000} + \frac{1}{1,000,000}
$$
$$
= \frac{10+2+5+5+1}{1,000,000\text{ hours}} = \frac{23}{1,000,000} = \frac{23,000}{1,000,000,000 \text{ hours}}
$$

or 23,000 FIT. The MTTF for the system is just the inverse of the failure rate:

$$
\text{MTTF}_{\text{ System}} = \frac{1}{\text{Failure rate System}} = \frac{1,000,000,000}{23,000} \approx 43,500 \text{ hours} \approx 5 \text{ years}
$$

* Redundancy (e.g., duplicated components or redoing operations) is key to coping with failure and improving system dependability. 
* Once a component is replaced and repaired, the system behaves as good as new.

# Example @ 47

 Suppose that we want to enhance the processor used for Web serving.
* The new processor is **10 times faster** on computation in the Web serving application than the original processor.
* Assuming that the original processor is:
    * busy with computation 40% of the time. 
    * waiting for I/O 60% of the time.
* What is the overall speedup gained by incorporating the enhancement?
### Answer
$$
\begin{align*}
\text{Fraction enhanced} &= 0.4;
\text{  Speedup enhanced} &= 10 \\
\text{Speedup overall} &= \frac{1}{0.6 + \frac{0.4}{10}} = \frac{1}{0.64} \approx 1.56
\end{align*}
$$

# Example @ 50

Suppose we have made the following measurements:
* Frequency of FP operations = 25%
* Average CPI of FP operations = 4.0
* Average CPI of other instructions = 1.33
* Frequency of FPSQR = 2%
* CPI of FPSQR = 20

Assume that the two design alternatives are:
* Decrease the CPI of FPSQR to 2, or
* Decrease the average CPI of all FP operations to 2.5.

Compare these two design alternatives using the processor performance equation.
### Answer
Step 1: Calculate original CPI

$$
\text{CPI}_{\text{ original}} = (25\% \times 4.0) + (75\% \times 1.33) = 1.0 + 1.0 = 2.0
$$

Step 2: CPI for alternative 1 (FPSQR improvement)

FPSQR is 2% of instructions. The CPI saving is:

$$
\begin{align*}
\text{CPI}_{\text{ with new FPSQR}} = \text{CPI}_{\text{ original}} * 2\% \times (\text{CPI}_{\text{ old FPSQR}} * \text{CPI}_{\text{ new FPSQR only}}) \\
= 2.0 * 0.02 \times (20 * 2) = 2.0 * 0.36 = 1.64
\end{align*}
$$

Step 3: CPI for alternative 2 (all FP instructions improved)

FP instructions have CPI reduced from 4.0 to 2.5, so:

$$
\text{CPI}_{\text{ new}} = (25\% \times 2.5) + (75\% \times 1.33) = 0.625 + 0.9975 = 1.6225 \approx 1.625
$$

Step 4: Compute speedups

Speedup is the ratio of original CPI to new CPI:

For alternative 1:

$$
\text{Speedup} = \frac{2.0}{1.64} \approx 1.22
$$

For alternative 2:

$$
\text{Speedup} = \frac{2.0}{1.625} \approx 1.23
$$

Conclusion:  
Both alternatives yield very similar speedups, about 1.22 to 1.23 times faster. The second alternative (improving all FP instructions) offers a slightly better speedup, though the difference is marginal. The choice should consider implementation complexity and cost.