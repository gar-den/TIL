# Algorithm

입력 받을 때는
    
    a, b = map(int, sys.stdin.readline().split())
    numbers = list(map(int, sys.stdin.readline().split()))



소수 구할 때는 [에라토스테네스의 체](https://velog.io/@htchoi1006/파이썬-에라토스테네스의-체)

    from math import sqrt

    max_num = 10000
    max_num += 1

    numbers = list(range(1, max_num+1))

    finish = int(sqrt(max_num))

    for i in range(2, finish + 1):
        if numbers[i] != False:
            for j in range(i*2, max_num, i):
                numbers[j] = False

    print([i for i in range(2, max_num) if numbers[i] != False])




최대공약수 구할 때는 [유클리드 호제법](https://ko.wikipedia.org/wiki/유클리드_호제법)

    if a < b:  # make a bigger
        a, b = b, a

    num1 = a
    num2 = b

    while num1 % num2 != 0:
        div = num1 % num2

        num1 = num2
        num2 = div

    biggest_divisor = num2




최소공배수 구할 때는

    biggest_divisor * (a // bigger_divisor) * (b // bigger_divisor)



팩토리얼 구할 때는

    def factorial(n):
        if n <= 1:
            return 1

        return n * factorial(n-1)
        
        
        
knapsack 문제는

    dp = [[0 for _ in range(kg+1)] for _ in range(n+1)]

    for i in range(1, n+1):
        for j in range(1, kg+1):
            if weights[i-1] > j:
                dp[i][j] = dp[i-1][j]
            else:
                dp[i][j] = max(dp[i-1][j - weights[i-1]] + values[i-1], dp[i-1][j])

    print(dp[n][kg])

