# LeetCode-1155.-Number-of-Dice-Rolls-With-Target-Sum

class Solution:
    def numRollsToTarget(self, n: int, k: int, target: int) -> int:
        def check(n,k,t):
            
            if (n,t) in d:
                return d[(n,t)]
            if n==1 and k>=t:
                d[(n,t)]=1
                return 1
            if n*k<t or n>t or n<=0:
                d[(n,t)]=0
                return 0
            c=0
            for x in range(1,k+1):
                t1=t-x
                if t1>=1:
                    c += check(n-1,k,t1) if (n-1,t1) not in d else d[(n-1,t1)]
            d[(n,t)]=c
            return d[(n,t)]

        d={}

        return check(n,k,target)%(10**9+7)
