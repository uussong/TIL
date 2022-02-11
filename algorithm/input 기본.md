# input 기본

```python
n = int(input()) # 정수 한 개 입력 받기
a, b = map(int, input().split()) # 정수 여러개 입력 받기

lst_1 = list(map(int, input.split(' '))) # 정수 형태를 일차원 리스트로 입력 받기
lst_2 = [map(int, input.split(' '))] # 리스트의 첫 번째 원소로 map object를 넣는 것 형변환 아님

numbers = list(input()) # ['1', '2', '3', '4']
numbers = list(map(int, list(input()))) # [1, 2, 3, 4] 띄어쓰기가 없는 정수 입력받아서 리스트 만들기

#2차원 배열
#grid or matrix: row 만들어놓고 col 채우는 것 생각
matrix = []
for _ in range(2):
    row = list(map(int, input().split())) # [1, 2, 3, 4] [5, 6, 7, 8]
    matrix.append(row)
print(matrix)

matrix_2 = [x for x in range(10)]
print(matrix_2) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

#이렇게도 할 수 있지만 그냥 위에것 쓰자
matrix = [list(map(int, input().split())) for _ in range(2)] # 앞에 것을 두 번 반복한다는 것 그 결과를 리스트에 원소로 넣음
print(matrix)

#얕은 복사와 깊은 복사
lst = [1, 2, 3, 4]
temp = []
temp.append(lst) # 리스트 자체를 어디에 할당하는 순간 얕은 복사 = 연동됨
temp.append((lst[:])) # 리스트에서 인덱스 슬라이싱은 원본을 바꾸는 것 아닌 새로운 메모리 형태에서 만들어진 것 반환, 깊은 복사 형태가 됨

lst.pop()
lst.insert(0, 5)

print(temp) # 얕은 복사 [[5, 1, 2, 3]] / # 깊은 복사 [[1, 2, 3, 4]]

lst = [[1, 2], [3, 4]]
temp = []
temp.append(lst[:]) # lst 통째가 복사되는 것 list 안에 list 자체의 메모리 주소값은 같음
                    # 2차원 이상이면 깊은 복사x 겉에 list만 복사 안에는 그대로 들고옴
                    # 그냥 import copy copy.deepcopy 써야..
lst[0][0] = 5

print(temp) # [[[5, 2], [3, 4]]]

#빈 matrix 만들기
zeros = [[0] * 5] * 5 # 얕은 복사
zeros[0][0] = 99
print(zeros)

zeros = []
for _ in range(5):
    row = [0] * 5 #[0, 0, 0, 0, 0] 매번 for문마다 row를 새로 만들고 있는 것
    zeros.append(row)
# zeros[0][0] = 99

for row in zeros:
    print(row)

zero_matrix = [[0] * 5 for _ in range(5)]

#리스트 사이에 리스트 넣기
lst = [1, 2, 3, 4]
lst[2:2] = ['a', 'b', 'c'] # [1, 2, 'a', 'b', 'c', 3, 4]
lst[1:3] = ['a', 'b'] # [1, 'a', 'b', 4]
lst[1:3] = ['a', 'b', 'c', 'd', 'e'] # [1, 'a', 'b', 'c', 'd', 'e', 'b', 'c', 3, 4]
print(lst)
```

