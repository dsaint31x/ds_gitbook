# Ch01.10 Linear Models in Business, Science, and Engineering

## 01.10.02 : Difference Equation

* In many fields, a dynamic system that changes over a time should be mathematically modeled. 
* Several features of the system are each measured at discrete time intervals, producing a sequence of vectors, $$ \textbf{x}_0, \textbf{x}_1, \textbf{x}_2, \cdots, $$. 
* The entries in $$\textbf{x}_k$$ provide information about the state of system at the time of the $$k$$th measurement.
* If there is a matrix $$A$$ such that $$\textbf{x}_1=A\textbf{x}_0, \textbf{x}_2=A\textbf{x}_1$$, and , in general 
$$
\textbf{x}_{k+1}=A\textbf{x}_k \text{  for }k=0,1,2,\cdots
$$
* then it is called a linear difference equation (or recurrence relation)
* Given such an equation, one can compute $$\textbf{x}_1,\textbf{x}_2$$, and so on, provided $$\textbf{x}_0$$ is known.
* The dicussion below illustrates how a difference equation might arise.
* A subject of interest to demographers is the movement of populations or groups of people from one region to another. The simple model here considers the changes in the population of a certain city and its surrounding suburbs over a period of years.
* Fix an initial year-say,2019- and denote the populations of the city and suburbs that year by $$r_0$$ and $$s_0$$, repectively. Let $$\textbf{x}_0$$ be the population vector
$$
\textbf{x}_0 = \begin{bmatrix}r_0 \\ s_0 \end{bmatrix}
\begin{matrix} \text{City population, 2019} \\ \text{Suburban population, 2019} \end{matrix}
$$
* For 2020 and subsequent years, denote the populations of the city and suburbs by vectors
$$
\textbf{x}_1 = \begin{bmatrix}r_1 \\ s_1 \end{bmatrix},
\textbf{x}_2 = \begin{bmatrix}r_2 \\ s_2 \end{bmatrix},
\textbf{x}_3 = \begin{bmatrix}r_3 \\ s_3 \end{bmatrix}
$$
* Our goal is to describe mathematically how these vectors might be related.
* Suppose demographic studies show that each year about 5% of the city's population moves to the suburbs (and 95% remains in the city), while 3% of the suburban populatoni moves to the city (and 97% remains in the suburs). See Fig.2 below:
![figure2](./fig/la_01_10_02.png)
* After 1 year, the original $$r_0$$ persons in the city are now distributed between city and suburbs as
$$
\begin{bmatrix}.95 r_0 \\.05 r_0\end{bmatrix} = r_0 
\begin{bmatrix}.95 \\ .05 \end{bmatrix}
\begin{matrix} \text{Remain in city} \\ \text{Move to suburbs} \end{matrix} \tag{6}
$$
* The so persons in the suburbs in 2019 are distributed 1 year later as
$$
s_0\begin{bmatrix}.03 \\.97 \end{bmatrix} 
\begin{matrix} \text{Move to city} \\ \text{Remain in suburbs} \end{matrix}
\tag{7}
$$
* The vectors in (6) and (7) account for all of the populations in 2020. Thus
$$
\begin{bmatrix} r_1 \\ s_1 \end{bmatrix}
=r_0\begin{bmatrix} .95 \\ .05 \end{bmatrix}
+s_0\begin{bmatrix} .03 \\ .97 \end{bmatrix}
=\begin{bmatrix} .95 &.03 \\ .05 & .97 \end{bmatrix}
\begin{bmatrix} r_0 \\ s_0 \end{bmatrix}
$$
* That is, 
$$
\textbf{x}_1 = M \textbf{x}_0 \tag{8}
$$
* Where $$M$$ is the migration matrix determined by the following table:
$$
M=\begin{bmatrix} .95 &.03 \\ .05 & .97 \end{bmatrix}
$$
* Equation (8) describes how the population changes
from 2019 to 2020. If the migration percentages
remain constant, then the change from 2020 to 2021
is given by
$$
\textbf{x}_2 = M \textbf{x}_1 
$$
* And similarly for 2021 to 2022 and subsequent years. In general,
$$
\textbf{x}_{k+1} = M\textbf{x}_k \text{ for }k=0,1,2,\cdots \tag{9}
$$
* The sequence of vectors $$\left\{ \textbf{x}_0, \textbf{x}_1, \textbf{x}_2, \cdots \right\}$$ describes the population of the city/suburban region over a period of years.


<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- ds_gitbook -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-3232161401562757"
     data-ad-slot="6357462623"
     data-ad-format="auto"
     data-full-width-responsive="true"></ins>
<script>
     (adsbygoogle = window.adsbygoogle || []).push({});
</script>
