---
aliases: 
---
# Public-Key Cryptography
---
This method used *two* kinds of keys, a public key and a private key. Every user has their own keys. The public key is known to everyone while the private key is kept secret. 

When you want to send a message to user A, you encrypt the message using public key A, and user A can decrypt it with their private key. This ensures that only user A can read the message or access the data. 

[[Public-key cryptography makes use of one-way functions]]. Here we will use a variety of the Rabin function. 

How would two users communicate using this sort of system?

Let's say we're using the equation `Y**X%P` as our translation function. At first, we let Y be equal to an arbitrary number, let's say 7 for now. If one user, 'Alice,' picks 10 as her private key, she can get a result of 4 from the above equation. 

If a second user, Bob, picks 2 as his private key, he gets a result of 10 from the translation equation.

Now, the two users exchange the 4 and 10, and plug this number into their translation functions, *but use their private keys in place of Y,* they will both arrive at the same number, three. 

This three can be used to encrypt the message, and even if you saw the exchange of the 10 and the 4, you can't decode the message without one of the private keys from a user.

Creating Alice's public key from her private key of 10:
```
alice_private = 10
y = 7
alice_public = y**alice_private%13
```

Creating Bob's public key from private key of 2:
```
bob_private = 2
y = 7
bob_public = y**bob_private%13
```

Now after the two users exchange keys, they change the value of `y` to their private keys and plug in the public key.

For Bob:
```
y = alice_public
bobs_key = y**bob_private%13
```

For Alice:
```
y = bob_public
bobs_key = y**alice_private%13
```

These two keys will be the same value, and can be used to translate between plaintext and ciphertext!