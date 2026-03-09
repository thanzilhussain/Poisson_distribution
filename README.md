# Fitting Poisson  distribution
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://user-images.githubusercontent.com/104613195/166248326-fd042076-8b0b-40c4-8b11-1d8e8fcb74db.png)

 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/166251988-d0c53205-6080-4f7b-ae4c-398178586637.png)

# Experiment :

![image](https://user-images.githubusercontent.com/103921593/230282876-f4a5afbf-cac1-4648-a1b0-c78840638a8e.png)

# Program :

Name : THANZIL HUSSAIN A
Reg No : 212225240169
Slot Name : T1-I5

```py
import numpy as np
import math
import scipy.stats


data = [int(i) for i in input("Enter the data with space: ").split()]
length = len(data)
M = max(data)
x = []
freq = []


for i in range(M+1):
    freq.append(data.count(i))
    x.append(i)

sum_freq = np.sum(freq)

p = [freq[i]/sum_freq for i in range(M+1)]


mean = np.inner(x, p)

print("X    P(X=x)    Obser.freq   Expec.freq  xi")
print()

chi = 0
for i in x:
    p_i = (math.exp(-mean) * (mean**i)) / math.factorial(i)
    e = p_i * sum_freq
    xi = ((freq[i] - e)**2) / e
    chi += xi
    print(f"{i}   {p_i:.3f}       {freq[i]}        {e:.2f}        {xi:.3f}")

print()
print("Calculated chi square value:", f"{chi:.4f}")


table_chi2 = scipy.stats.chi2.ppf(1 - 0.01, df=M)
print(f"Table value of chi square at 1% level is {table_chi2:.4f}")

if chi < table_chi2:
    print("✔ The data can be fitted in Poisson Distribution at 1% LOS")
else:
    print("✘ The data cannot be fitted in Poisson Distribution at 1% LOS")
```


# Output : 

<img width="965" height="381" alt="image" src="https://github.com/user-attachments/assets/c578ac3b-e048-43f1-978b-51d0494e70ba" />

# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
