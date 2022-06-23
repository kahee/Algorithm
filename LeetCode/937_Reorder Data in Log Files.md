## 937. Reorder Data in Log Files
https://leetcode.com/problems/reorder-data-in-log-files/

### 문제 풀이 - 해결 못해서 책봄 
- Furthermore, the key could be a tuple of multiple keys, i.e. tuple(key_1, key_2, ... key_n).
- sort key 여러개 하는건 처음 알았다.. tuple 형식으로 넘기는듯
- https://blog.naver.com/PostView.nhn?isHttpsRedirect=true&blogId=wideeyed&logNo=221745416992&redirect=Dlog&widgetTypeCall=true&directAccess=false
- sort: 리스트 값 변환 vs sorted: 반환 

```python 
class Solution:
    def reorderLogFiles(self, logs: List[str]) -> List[str]:
        # 각 빈칸으로 나눔 그리고 [2] 번째중에 가장 높은거 
        # 영문과 숫자로 나눔 
        # splict sort -> 만약 같으면 식별자로 구분..?        
        
        letters = []
        digits = []
        for num, log in enumerate(logs):
            log_list = log.split()
            
            if log_list[1].isdigit():
                digits.append(log)
            else:
                letters.append(log)
            
        letters.sort(key=lambda x: (x.split()[1:], x.split()[0]))
        return letters + digits
        
```

### 내 풀이 

- 막힌 테스트 케이스: `["a1 9 2 3 1","g1 act car","zo4 4 7","ab1 off key dog","a8 act zoo","a2 act car"]`
- 문자열이 같은 경우 식별자로 한번더 비교해야하는데 이부분에서 막힘...

```python 
class Solution:
    def reorderLogFiles(self, logs: List[str]) -> List[str]:
        # 각 빈칸으로 나눔 그리고 [2] 번째중에 가장 높은거 
        # 영문과 숫자로 나눔 
        # splict sort -> 만약 같으면 식별자로 구분..?        
        
        letters = []
        digits = []
        result = []
        for num, log in enumerate(logs):
            log_list = log.split()
            
            if log_list[1].isdigit():
                digits.append(log)
            else:
                letters.append((' '.join(log_list[1:]), num))
                
        
        for letter, num in sorted(letters):
            result.append(logs[num])
            
        result.extend(digits)
        return result
            

        
```