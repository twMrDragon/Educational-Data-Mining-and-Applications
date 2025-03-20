# 教育數據探勘與應用 hw2

## 資工三 111590012 林品緯

### 4.3

#### (a)

1. 設 $I$ 為一個 frequent itemset，即支持度大於或等於支持度閾值
2. 設 $S$ 為 $I$ 的任意 subset
3. 因為每個出現 $I$ 的的紀錄包含 $S$，所以 $S$ 的支持度至少和 $S$ 一樣
4. 因為 $I$ 支持度大於或等於支持度閾值，所以 $S$ 支持度也大於或等於支持度閾值
5. 因此一個 frequent itemset 的所有 noneempty subsets 都會 frequent

#### (b)

1. 設 $s$ 為一個 itemset 且 $s'$ 為 $s$ 的任意 subsets
2. 每個出現 $s$ 的紀錄一定包含 $s'$，因此 $s'$ 的支持度只少和 $s$ 一樣
3. 所以 $s'$ 的支持度會大於等於 $s$

#### (c)

1. $l$ 為 itemset，且 $s$ 為 $l$ 的 subset 和 $s'$ 為 $s$ 的 subset
2. $s\rightarrow(l-s)$ 的 confidence 為:
   $$
   \begin{aligned}
   \text{Confidence}(s\rightarrow(l-s)) = \frac{\text{support}(l)}{\text{support}(s)}
   \end{aligned}
   $$
3. $s'\rightarrow(l-s')$ 的 confidence 為:
   $$
   \begin{aligned}
   \text{Confidence}(s'\rightarrow(l-s')) = \frac{\text{support}(l)}{\text{support}(s')}
   \end{aligned}
   $$
4. 因為 $s'$ 為 $s$ 的 subset，根據 (b) 得出:
   $$
   \begin{aligned}
       \text{support}(s') \geq \text{support}(s)
   \end{aligned}
   $$
5. 因此:
   $$
   \begin{aligned}
   \frac{\text{support}(l)}{\text{support}(s')} \leq \frac{\text{support}(l)}{\text{support}(s)}
   \end{aligned}
   $$
6. 所以 $s'\rightarrow(l-s')$ 的 confidence 不會大於 $s\rightarrow(l-s)$ 的 confidence

#### (d)

1. 設 $D$ 為整個資料庫，總共有 $T$ 比資料
2. 將 $D$ 分為 $n$ 個不重疊分區 $D_1、D_2、\cdots、D_n$
3. 設 X 在 D 中為 frequent itemset，即支持度大於或等於支持度閾值 $\sigma$
4. X 在 D 中的支持度為:
   $$
   \begin{aligned}
   \text{support}(X,D) &= \frac{\sum^{n}_{i=1} X \text{ 在 } D_i \text{ 的數量} }{T} \\
   &=\sum^{n}_{i=1}\text{support}(X,D_i)\times\frac{|D_i|}{T}
   \end{aligned}
   $$
5. 假設 X 在每個分區 $D_i$ 都不 frequent，即 $\text{support}(X,D_i)\lt\sigma$
6. 因此 X 在 D 的總支持度為:
   $$
   \begin{aligned}
   \text{support}(X,D)=\sum^{N}_{i=1}\text{support}(X,D_i)\times\frac{|D_i|}{T}\lt\sum^{n}_{i=1}\sigma\times\frac{|D_i|}{T} = \sigma
   \end{aligned}
   $$
7. 這導致 $\text{support}(X,D) \lt \sigma$，與一開始的假設 ( X 在 D 中 frequent) 矛盾
8. 所以如果 $X$ 在 $D$ 中 frequent，那麼 $X$ 至少有一個分區 $D_i$ 是 frequent

### 4.8

#### (a)

| item   | frequency |
| ------ | --------- |
| Milk   | 4         |
| Cheese | 3         |
| Bread  | 4         |
| Crab   | 1         |
| Apple  | 2         |
| Pie    | 2         |

frequent 1-itemsets

| itemset  | support             |
| -------- | ------------------- |
| {Milk}   | $\frac{4}{4}=100\%$ |
| {Cheese} | $\frac{3}{4}=75\%$  |
| {Bread}  | $\frac{4}{4}=100\%$ |

frequent 2-itemsets

| itemset        | support             |
| -------------- | ------------------- |
| {Milk,Cheese}  | $\frac{3}{4}=75\%$  |
| {Cheese,Bread} | $\frac{3}{4}=75\%$  |
| {Bread,Milk}   | $\frac{4}{4}=100\%$ |

frequent 3-itemsets

| itemset             | support            |
| ------------------- | ------------------ |
| {Milk,Cheese,Bread} | $\frac{3}{4}=75\%$ |

Ans:<br>

Larget k = 3

support({Milk,Cheese,Bread}) = $\frac{3}{4}=75\%$

confidence:

$\{\text{Milk,Cheese}\}\rightarrow\{\text{Bread}\} = \frac{3}{4}$

$\{\text{Milk,Bread}\}\rightarrow\{\text{Cheese}\} = \frac{3}{3}$

$\{\text{Bread,Cheese}\}\rightarrow\{\text{Milk}\} = \frac{3}{4}$

#### (b)

| item             | frequency |
| ---------------- | --------- |
| Dairyland-Milk   | 2         |
| Sunset-Milk      | 2         |
| Dairyland-Cheese | 2         |
| Best-Bread       | 1         |
| Wonder-Bread     | 3         |
| Tasty-Pie        | 2         |
| Goldenfarm-Apple | 1         |
| Westcoast-Apple  | 1         |
| King’s-Crab      | 1         |
| Best-Cheese      | 1         |

frequent 1-itemsets

| itemset        | support            |
| -------------- | ------------------ |
| {Wonder-Bread} | $\frac{3}{4}=75\%$ |

Larget k = 1

support({Wonder-Bread}) = $\frac{3}{4}=75\%$

### 4.14

#### (a)

support(hot dogs) = $\frac{3000}{5000} = 60\% \gt 25\%$

support(hamburgers) = $\frac{2500}{5000} = 50\% \gt 25\%$

confidence(hot dogs $\rightarrow$ hamburgers) = $\frac{\frac{2000}{5000}}{\frac{3000}{5000}}=\frac{2}{3}\gt50\%$

This association rule is strong.

#### (b)

$P(\text{hot dogs}) = \frac{3000}{5000}=0.6$

$P(\text{hamburgers}) = \frac{2500}{5000}=0.5$

$P(\text{hot dogs}\cap\text{hamburgers}) = \frac{2000}{5000}=0.4$

$P(\text{hot dogs})\times P(\text{hamburgers}) = 0.3$

$P(\text{hot dogs}\cap\text{hamburgers})\neq P(\text{hot dogs})\times P(\text{hamburgers})$

Not independent

Positive correlation

#### (c)

|               | hot dogs | !(hot dogs) | total |
| ------------- | -------- | ----------- | ----- |
| hamburgers    | 2000     | 500         | 2500  |
| !(hamburgers) | 1000     | 1500        | 2500  |
| Total         | 3000     | 2000        | 5000  |

| rule                                    | confidence                      |
| --------------------------------------- | ------------------------------- |
| hot dogs $\rightarrow$ hamburgers       | $\frac{2000}{3000}=\frac{2}{3}$ |
| hamburgers $\rightarrow$ hot dogs       | $\frac{2000}{2500}=\frac{4}{5}$ |
| hot dogs $\rightarrow$ !(hamburgers)    | $\frac{1000}{3000}=\frac{1}{3}$ |
| !(hamburgers) $\rightarrow$ hot dogs    | $\frac{1000}{2500}=\frac{2}{5}$ |
| !(hot dogs) $\rightarrow$ hamburgers    | $\frac{500}{2000}=\frac{1}{4}$  |
| hamburgers $\rightarrow$ !(hot dogs)    | $\frac{500}{2500}=\frac{1}{5}$  |
| !(hot dogs) $\rightarrow$ !(hamburgers) | $\frac{1500}{2000}=\frac{3}{4}$ |
| !(hamburgers) $\rightarrow$ !(hot dogs) | $\frac{1500}{2500}=\frac{3}{5}$ |

| P             | hot dogs | !(hot dogs) | total |
| ------------- | -------- | ----------- | ----- |
| hamburgers    | 0.4      | 0.1         | 0.5   |
| !(hamburgers) | 0.2      | 0.3         | 0.5   |
| Total         | 0.6      | 0.4         | 1.0   |

|                | hot dogs $\rightarrow$ hamburgers            | hot dogs $\rightarrow$ !(hamburgers)         | !(hot dogs) $\rightarrow$ hamburgers         | !(hot dogs) $\rightarrow$ !(hamburgers)      |
| -------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| all_confidence | $\frac{2}{3}$                                | $\frac{1}{3}$                                | $\frac{1}{5}$                                | $\frac{3}{5}$                                |
| max_confidence | $\frac{4}{5}$                                | $\frac{2}{5}$                                | $\frac{1}{4}$                                | $\frac{3}{4}$                                |
| Kulczynski     | $\frac{1}{2}\times(\frac{2}{3}+\frac{4}{5})$ | $\frac{1}{2}\times(\frac{1}{3}+\frac{2}{5})$ | $\frac{1}{2}\times(\frac{1}{5}+\frac{1}{4})$ | $\frac{1}{2}\times(\frac{3}{5}+\frac{3}{4})$ |
| cosine         | $\frac{0.4}{\sqrt{0.6\times0.5}}=0.73$       | $\frac{0.2}{\sqrt{0.6\times0.5}}=0.37$       | $\frac{0.1}{\sqrt{0.4\times0.5}}=0.22$       | $\frac{0.3}{\sqrt{0.4\times0.5}}=0.67$       |
| lift           | $\frac{0.4}{0.6\times0.5}=\frac{4}{3}$       | $\frac{0.2}{0.6\times0.5}=\frac{2}{3}$       | $\frac{0.1}{0.4\times0.5}=\frac{1}{2}$       | $\frac{0.3}{0.4\times0.5}=\frac{3}{2}$       |
| correlation    | positive                                     | negative                                     | negative                                     | postive                                      |
