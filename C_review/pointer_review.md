# Pointer

- 1차원 / n차원
- 1 차 원 / n 차 원 
- 할 당 / 출 력 / 함 수
- 선 언 / 건 네 주 기 
  - **&는 값이 담긴 주소값의 반환**
    - (배열 이름)은 첫 주소 값을 의미합니다.
  - **\*은 변수가 가리키고 있는 값**
    - (배열이름/포인터이름[n])은 주소가 가리키는 값의 반환을 의미합니다.
  - **심지어 포인터 또한 포인터 값을 갖습니다.**
    - 포인터의 포인터값이 가리키는 주소 속의 값은 원래 포인터의 값입니다.
    - 모든 변수들은 포인터 값을 갖기 떄문입니다.
  - **포인터 값은 정수형(int형)이 아니다.**
    - 정수병 변수의 포인터라면, 포인터가 가리키는 값이 정수형인 것. 
  - **포인터 이름과 함수 이름이 겹친다면 함수가 동작하지 않을 수 있다. (변수명이 함수명보다 우선순위!)**
	
<p align="center"><img src="https://user-images.githubusercontent.com/59442344/157832062-41419096-bd18-49ed-bd65-9bf1e4e318a6.png" width="60%"></p>

	
	
## 1 차 원
	
### 할 당

- **포인터 선언**

```cpp
// 포인터 값 선언
char *p
int *p;
```

- **포인터 변수와 일반 변수**
  - 포인터, 일반변수
  - 포인터, 배열
  - 포인터, 문자열

```cpp
// 변수에 포인터 값 할당
int num = *p

void swap(int *n, int *m) {
  int tmp = *n;
  *n = *m;
  *m = tmp;
}

// 포인터에 변수 주소 할당
int a;
int *p = &a;

// 포인터에 배열 주소 할당
int *p;
int arr[10];
p = arr;
p = &arr[0];
p = &arr[1];

// 배열의 특정 위치를 가리키는 여러가지 방법
p[2] == *(p + 2)
&p[2] == (p + 2)

// 문자열과 포인터 : scanf()로 문자열 받아들이기
char arr[10];
scanf("%s", arr); 
```

- **동적할당 (int형 배열의 예)**

```cpp
// malloc
int *arr = (int *)malloc( sizeof(int) * len );

// calloc
int *arr = (int *)calloc( sizeof(int) , len );

// realloc
arr = realloc(arr, Modified_Len * sizeof(int) );

// free
free(arr);
```

### 출력

- **정수, 문자 출력**

```cpp
// 정수 포인터 변수와 출력
int *p;
printf(" %d ", *p);
printf(" %d ", p);
printf(" %p ", p);

// 문자 포인터 변수와 출력

```

- **문자열의 출력 (결국 배열)**

```cpp
// 문자열 포인터 변수와 출력

// 선언 후 읽기O, 수정X : (1) ksd vsdf / (2) k
char *p = "ksd vsdf";
printf("%s", p);
printf("%c", *p);

// 선언 후 읽기O, 수정O
char arr[100];
printf("%s", arr);
```

- **문자열 메모리 주소 출력**

```cpp
int arr[10];
int *p;
p = &arr[1];
printf("%d %d", arr[1], p[0]);
```

### 함수

- **함수 인자 건네기**

```cpp
// 변수의 주소값 건넴
function( &num )

// 배열의 측정 값을 건넴
function( &array[0] )

// 배열의 주소를 건넴(첫 번째 배열 공간의 주소)
function( array )
```

- **함수 매개변수 선언**

```cpp
// 정수 변수 주소 줘라
function(int *p)

// 고정 배열을 주소값으로 참조
function(int array[])

// 동적 배열을 주소값으로 참조
function(int array[*])
```

## n 차원

- **포인터 선언**

```cpp
// 포인터 선언
char **p;
int **p;
```

- **다차원 배열과 포인터 표현**

```cpp
int arr[3][3];

arr[3][1] == *(arr[3]+1) == *(*(arr+3)+1);
```

- **2차원 동적할당**

```cpp
int **table;

// row
table = (int **)malloc(sizeof(int *) * row);

// col
for(int i=0; i<row; ++i){
  table[i] = (int *)malloc(sizeof(int) * col);
}
```

- **2차원 동적할당의 해제**

```cpp
// col
for(int i=0; i<col; ++i){
  free(table[i]);
}

// row
free(table);
```

## MISC.

- **char * c : 문자열을 런타임에 넣을 수 없다. char형 변수의 포인터 이기 때문이다.**
- **char * c = "dsjfls ksdf" 로 선언과 동시에 초기화하는 것은 가능**
- **char c[] = "Hello world!"; : 배열을 선언과 동시에 초기화한다면, 배열의 길이 선언을 생략 할 수 있다.**

		  
