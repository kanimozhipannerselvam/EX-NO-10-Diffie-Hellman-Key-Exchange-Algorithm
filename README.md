![image](https://github.com/user-attachments/assets/b7b56e4d-e2f8-4645-a3e5-a000f37dceac)# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>
#include <math.h>

int modExp(int base, int exp, int mod) {
    int result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
   
    int p = 23;  
    int g = 5;   
    
    int a, b;
    printf("Enter Alice's private key: ");
    scanf("%d", &a);
    printf("Enter Bob's private key: ");
    scanf("%d", &b);
    
    int A = modExp(g, a, p);  
    int B = modExp(g, b, p);  
    
    printf("Alice's Public Key: %d\n", A);
    printf("Bob's Public Key: %d\n", B);
    
   
    int sharedKeyAlice = modExp(B, a, p);  
 
    int sharedKeyBob = modExp(A, b, p);   
    
    printf("Shared Secret Key (Alice): %d\n", sharedKeyAlice);
    printf("Shared Secret Key (Bob): %d\n", sharedKeyBob);
    
    if (sharedKeyAlice == sharedKeyBob) {
        printf("Key Exchange Successful! Shared Secret Key: %d\n", sharedKeyAlice);
    } else {
        printf("Key Exchange Failed!\n");
    }
    return 0;
}

```





## Output:
![image](https://github.com/user-attachments/assets/2f17bf04-3b13-4e2c-99fd-441ab82d1df0)




## Result:
  The program is executed successfully

