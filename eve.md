# Assignment 4 - Eve - Noah Lee - September 27th 2024

## What you (Eve) intercepted for Diffie Hellman
* Alice and Bob agree on g = 7 and p = 97.
* Alice sent Bob the number 53 (A).
* Bob sent Alice the number 82 (B).

## Your job for Diffie Hellman
1. Figure out the shared secret agreed upon by Alice and Bob. This will be an integer.
2. Show your work. Exactly how did you figure out the shared secret?
3. Show precisely where in your process you would have failed if the integers involved were much larger.

### Q1 & 2
Alice:
A = 7^a%97=53

Run the following python script (exhaustive check):
for num in range(1,97):
    if (7**num)%97==53:
        print(num)
        break

a = 22

Bob: 
B = 7^b%97=82

Run the following python script (exhaustive check):
for num in range(1,97):
    if (7**num)%97==82:
        print(num)
        break
b = 41

K = 7**(22*41)%97 = 65
Shared key is 65.

### Q3
'Run the following python script (exhaustive check)'
The process would be halted here if g and p were large prime integers because the exhaustive check would involve checking every number up until there for both a and b which would take an extremely long time and would not be feasible even with heavy computational power.


## What you, Eve, intercepted for RSA
* Bob's public key: (e_Bob, n_Bob) = (13, 162991)
Here's the encrypted data sent from Alice to Bob:
[17645, 100861, 96754, 160977, 120780, 90338, 130962, 74096,
128123, 25052, 119569, 39404, 6697, 82550, 126667, 151824,
80067, 75272, 72641, 43884, 5579, 29857, 33449, 46274,
59283, 109287, 22623, 84902, 6161, 109039, 75094, 56614,
13649, 120780, 133707, 66992, 128221]

## Your job for RSA
1. Figure out the encrypted message sent from Alice to Bob.
2. Show your work. Exactly how did you figure out the message? (You should include an explanation of how the message from Alice to Bob is encoded. That is, how does Alice's intended message (whatever manner of message it may be) correspond to the integers in the plaintext that you end up with after decrypting the encrypted message?)
3. Show precisely where in your process you would have failed if the integers involved were much larger.
4. Explain, briefly, why the message encoding Alice used would be insecure even if Bob's keys involved larger integers.


### Q1 & 2
Find Bob's p and q:
n_bob = 162991
Run following python script:
for i in range(1,162991):
    if 162991%i==0:
        print(i)
1
389
419

p = 389
q = 419

$\lambda(n_B)$ = lcm(388, 418) = 81904 (google searched lcm(388,418))

Python code to get $d_b$:

for i in range(1,81904):
    if (13*i)%81904==1:
        print(i)

$d_b=18901$

#### Decrypting the message:
enc_data = [17645, 100861, 96754, 160977, 120780, 90338, 130962, 74096,
128123, 25052, 119569, 39404, 6697, 82550, 126667, 151824,
80067, 75272, 72641, 43884, 5579, 29857, 33449, 46274,
59283, 109287, 22623, 84902, 6161, 109039, 75094, 56614,
13649, 120780, 133707, 66992, 128221]

dec_data = []
for i in enc_data:
    new_int = (i**18901)%162991
    dec_data.append(new_int)

dec_data = [134559, 33707, 9483, 120431, 74139, 66403, 31861, 145885, 81984, 130967, 39902, 82194, 59587, 110527, 43309, 159032, 99140, 74921, 121188, 49337, 69146, 106402, 44329, 16313, 115924, 53301, 153628, 5988, 40759, 14339, 68878, 105129, 60816, 74139, 81194, 36636, 91253]

Translated to text: it looks like garbage - the Nb is also extremely large so the numbers don't seem to represent ASCII. Perhaps this data is additionally encoded via AES using the K=65 from earlier.

Sorry I can't figure out what to do now - I will go to office hours on Monday to figure it out - 9/28/2024


