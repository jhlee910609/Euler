> Given an integer `n`, find the value of `phi(n)`, where `phi` is [Euler's totient function](keyword://eulers-totient-phi-function).
>
> **Example**
>
> For `n = 5`, the output should be
> `eulersTotientFunction(n) = 4`.

### 문제 : 오일러의 피(phi)함수를 활용하여 phi(n)의 값을 구하라

![](http://cfs6.blog.daum.net/image/22/blog/2007/06/14/22/34/467143cd227df&filename=20070612095807_532_1.jpg)


### 1. 오일러의 피함수

> **오일러 φ 함수**(Euler φ 函數, [영어](https://ko.wikipedia.org/wiki/%EC%98%81%EC%96%B4): Euler’s phi (totient) function)는 1부터 n까지의 양의 [정수](https://ko.wikipedia.org/wiki/%EC%A0%95%EC%88%98) 중에 n과 [서로소](https://ko.wikipedia.org/wiki/%EC%84%9C%EB%A1%9C%EC%86%8C_(%EC%88%98%EB%A1%A0))인 것의 개수를 나타내는 함수 [출처 : 위키피디아]

- 1, 2, 3, 4, 5, 6 중에, 6과 서로소인 수는 1, 5 두 개이다. 따라서, φ(6) = 2
- 1, 2, 3, 4, 5, 6, 7 중에, 7 이외에는 모두 7과 서로소이다. 따라서, φ(7) =6

### 2. 서로소

> 최대공약수가 1인, 둘 이상의 양의 정수들은 서로소(relatively prime)이라고 불린다.[[1\]](https://ko.wikipedia.org/wiki/%EC%84%9C%EB%A1%9C%EC%86%8C_(%EC%88%98%EB%A1%A0)#cite_note-1) 두 정수가 1 이외에 양의 공약수를 가지지 않으면 서로소이다.

### [문제 재정의]

### 1부터 n까지 양의 정수 중 n과 최대 공약수가 1인 양의 정수들의 개수를 구하여라.

```java
int eulersTotientFunction(int n) {
	    		// n과 서로소인 정수 개수를를 저장하는 total
		        int total = 0;
  
  				// n이 1일 때, 1의 약수는 1 밖에 없으니 1 리턴한다. 
		        if (n == 1) return 1;
  
  				// for문을 [i = 1] 부터 [i < n]까지 돌린다.
		        for (int i = 1; i < n; i++) {
		        	// 공약수의 개수를 저장하는 count   
		            int count = 0;
                  	
                  	// ========[ 공약수 구하는 로직 ]======
             
		            for (int j = 1; j <= i; j++) {
			    
                           // n의 약수     &&  i의 약수 
		            	 if (n % j == 0 && i % j == 0) count++;
		            }
			    
                    // 공약수의 개수가 1개면 최대공약수가 1인 서로소 일 수 밖에 없음
		            if (count == 1) total++;
		        }
		        return total;
		    }
```
