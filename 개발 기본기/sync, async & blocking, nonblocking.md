### sync, async
caller가 작업 완료를 기다리는 방식
>sync: caller가 작업 완료를 기다림<br>
>async: caller가 작업 완료를 기다리지 않고 다른 일을 함

### blocking, nonblocking
callee가 제어권을 언제 돌려주는가?
>blocking: callee가 작업이 완료될 때까지 제어권을 돌려주지 않음<br>
>nonBlocking: callee가 작업 완료와 무관하게 즉시 제어권을 돌려줌

### 조합
2 * 2로 4가지 방식이 존재할 수 있으나<br>
압도적으로 많이 쓰이는 조합은 sync + blocking과 async + nonBlocking

1) sync + blocking

특징:
- 코드가 직관적이고 이해하기 쉬움(순차로직)
- 에러 처리가 단순함

예시:
```
# 파일 읽기 - 읽을 때까지 프로그램이 멈춤
with open('large_file.txt', 'r') as f:
    content = f.read()  # 여기서 블로킹됨
print("파일 읽기 완료")  # 위 작업이 끝나야 실행됨
```

2) async + nonBlocking

특징:
- 높은 동시처리 성능(특히 IO Bound 작업)
- 리소스 활용 효율성 높음

예시:
```
// JavaScript - 가장 일반적인 비동기 패턴
async function processFiles() {
    const promise1 = fs.promises.readFile('file1.txt');
    const promise2 = fs.promises.readFile('file2.txt');
    
    // 두 파일을 동시에 읽기 시작하고 다른 일 가능
    doOtherWork();
    
    const [content1, content2] = await Promise.all([promise1, promise2]);
}
```

3) sync + nonBlocking
-> 데이터를 polling하는 작업

4) async + blocking
-> 비동기 요청이 blocking으로 인해 장점을 잃은 형태

### 추가 작성 예정 내용
- Nginx나 NodeJS 엔진이 어떻게 async + nonBlocking으로 동작하는지 작성 

