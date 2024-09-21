# **Assignment 1**

**Name:** _Harkeerat Singh Sawhney_

**Date:** 27. October. 2021

## **Exercise 1 - Amdahl's Law**

### **Question 1:**

### **(a):**

Formula for Speed Up is as follows:

$$S_4 = T_1 / T_4, \newline$$

hence the formula for execution time on **4** processors:

$$T_4 = \left[0.10 \times T_1 + \left(\frac{0.9}{4} \times T_1\right)\right]. \newline$$

Hence,

$$S_4 = \frac{T_1}{0.10T_1 + \frac{0.9}{4}T_1} = \frac{1}{0.10 + \frac{0.9}{4}} \pmb{\approx 3.077}. \newline \newline$$

Therefore,

$$E_4 = \frac{S_4}{4} = \frac{3.077}{4} \pmb{\approx 0.768}$$

### **(b):**

Formula for Speed Up is as follows:

$$S_8 = T_1 / T_8, \newline$$

hence the formula for execution time on **8** processors:

$$T_8 = \left[0.10 \times T_1 + \left(\frac{0.9}{8} \times T_1\right)\right]. \newline$$

Hence,

$$S_8 = \frac{T_1}{0.10T_1 + \frac{0.9}{8}T_1} = \frac{1}{0.10 + \frac{0.9}{8}} \pmb{\approx 4.706}. \newline \newline$$

Therefore,

$$E_8 = \frac{S_4}{8} = \frac{4.705}{8} \pmb{\approx 0.588}$$

### **(c):**

Formula for Speed Up is as follows:

$$S_{16} = T_1 / T_{16}, \newline$$

hence the formula for execution time on **8** processors:

$$T_{16} = \left[0.10 \times T_1 + \left(\frac{0.9}{16} \times T_1\right)\right]. \newline$$

Hence,

$$S_{16} = \frac{T_1}{0.10T_1 + \frac{0.9}{16}T_1} = \frac{1}{0.10 + \frac{0.9}{16}} \pmb{\approx 6.4}. \newline \newline$$

Therefore,

$$E_8 = \frac{S_4}{16} = \frac{6.4}{16} \pmb{= 0.4}$$

### **Question 2:**

### **(a):**

$$S_8 = \frac{T_1}{T_8} = \frac{T_1}{\left((1-0.2)T_1 \space + \frac{0.2}{8}T_1 \right)} = \frac{1}{\left(0.8 + \frac{0.2}{8}\right)} \approx \pmb{1.212}$$

### **(b):**

$$S_4 = \frac{T_1}{T_4} = \frac{T_1}{\left((1-0.5)T_1 \space + \frac{0.5}{4}T_1 \right)} = \frac{1}{\left(0.5 + \frac{0.5}{4}\right)} \approx \pmb{1.6}$$

Hence option `(b)` should be selected on the basis of **1.212 < 1.6** if the performance is the primary concern.

### **Question 3:**

Since,

$$\lim_{n \to \infty} S_n = \lim_{n \to \infty} \frac{1}{\left(0.9 + \frac{0.1}{n}\right)} = \frac{1}{0.9 + 0} = \frac{1}{0.9}.$$

Therefore,

$$\lim_{n \to \infty} S_n \approx \pmb{1.11}$$

## **Exercise 2 - Parallel Summation - Thread Safety**

### **Question 1:**

### **1.1**

CDAB

### **1.2**

ACDB and the value would be 5

### **Question 2:**

The class `SumMutlipleUpdates` is designed in such way that every instance of that class synchronizes with the method `.run()` only on its instance. Hence, it means that this is not synchronized since it doesn't have a common lock.

Also the method `.addPartialResult` is designed in such way that multiple threads could enter it during a critical time. When that happens it would change the whole outcome, which by default makes this design not thread safe.

### **Question 4:**

By using the keyword volatile it allows the threads to read and write into the main memory, hence it does not solve any races. So hence, that means that result value will be visible to the all the threads in the same way. However, the access to the value is not synchronized, which ends up making the field consistent. This leads to the values in it not always correct.

### **Question 7:**

The circumstances in which the sequential version of the summation may perform better than the parallel versions is when the number of threads in the operations is too small. Hence, if such situations exists then the parallel execution would produce either a much more worse performance or as same as the sequential execution.

Also in parallel version due to a small number of threads means that the machine would be overwhelmed with the tasks such as creation, execution, scheduling and killing the threads. This would then eliminate all the advantages which were gained by the parallel execution.

Another reason is that the summation may perform better is than the parallel version is due the simplicity, since creating threads and initializing a multi-thread structure tends to takes time.