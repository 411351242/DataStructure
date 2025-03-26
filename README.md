###DATA STRUCTURE HW1
## 1.What problem is the `teams()` function primarily solving?

**目標：**

- 利用遞迴輸入集合或元素，輸出其基本單位的可能組合。

**Arguments：**

- **candidates**：輸入的集合或元素
- **k**：幾個基本單位為一組

---

## 2.What result will be produced when executing `teams(['ABTZ'], 2)` ?

**Output：**

- `[]`

---

## 3.Please provide other examples of inputs for candidates and k.

**Input：**

```python
a = ['sdk','ahl','ew','iut']
b = 'asdfgl'

for i in range(4):
    print(teams(a, i+1))
for i in range(6):
    print(teams(b, i+1))
```

**Output：**

- a：
    1. `['sdk', 'ahl', 'ew', 'iut']`
    2. `['sdkahl', 'sdkew', 'sdkiut', 'ahlew', 'ahliut', 'ewiut']`
    3. `['sdkahlew', 'sdkahliut', 'sdkewiut', 'ahlewiut']`
    4. `['sdkahlewiut']`
- b：
    1. `['a', 's', 'd', 'f', 'g', 'l']`
    2. `['as', 'ad', 'af', 'ag', 'al', 'sd', 'sf', 'sg', 'sl', 'df', 'dg', 'dl', 'fg', 'fl', 'gl']`
    3. `['asd', 'asf', 'asg', 'asl', 'adf', 'adg', 'adl', 'afg', 'afl', 'agl', 'sdf', 'sdg', 'sdl', 'sfg', 'sfl', 'sgl', 'dfg', 'dfl', 'dgl', 'fgl']`
    4. `['asdf', 'asdg', 'asdl', 'asfg', 'asfl', 'asgl', 'adfg', 'adfl', 'adgl', 'afgl', 'sdfg', 'sdfl', 'sdgl', 'sfgl', 'dfgl']`
    5. `['asdfg', 'asdfl', 'asdgl', 'asfgl', 'adfgl', 'sdfgl']`
    6. `['asdfgl']`

<aside>
💡

對於 list，字串視為一個單位

對於字串，每個字元視為一個單位

</aside>

## 4.Please write appropriate comments for the following code.

```python
def teams(candidates, k):		# 利用遞迴輸入集合或元素，輸出其基本單位的可能組合
												    # Argument:
												    # - candidates: 輸入的集合或元素
												    # - k: 幾個基本單位為一組
    if k == 0:                                 #如果k=0，回傳空list
        return ['']
        
    if len(candidates) == 0:                   #如果輸入的集合或元素長度=0，回傳空list
        return []
        
    result = []                                #初始化輸出結果，用來存放可能的組合
    
    for team in teams(candidates[1:], k - 1):  #從第一個單位元素以外,剩下的單位元素中,
        result.append(candidates[0] + team)    #找到第一個單位元素與剩下的單位元素的組合

    result += teams(candidates[1:], k)         #藉由每次排除第一個單位元素的方式,
                                               #呼叫自己重複直到找到所有單位元素的組合
    return result                              #回傳結果
```
