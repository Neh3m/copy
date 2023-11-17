# vignere cypher 

def generateKey(string, key):
    key = list(key)
    if len(string) == len(key):
        return(key)
    else:
        for i in range(len(string) -
                       len(key)):
            key.append(key[i % len(key)])
    return("" . join(key))

def cipherText(string, key):
    cipher_text = []
    for i in range(len(string)):
        x = (ord(string[i]) +
             ord(key[i])) % 26
        x += ord('A')
        cipher_text.append(chr(x))
    return("" . join(cipher_text))
def originalText(cipher_text, key):
    orig_text = []
    for i in range(len(cipher_text)):
        x = (ord(cipher_text[i]) -
             ord(key[i]) + 26) % 26
        x += ord('A')
        orig_text.append(chr(x))
    return("" . join(orig_text))

# ceaser cypher 

def encrypt(text,s):
    result = ""
    for i in range(len(text)):
        char = text[i]
        if (char.isupper()):
            result += chr((ord(char) + s-65) % 26 + 65)
        else:
            result += chr((ord(char) + s - 97) % 26 + 97)
    return result
text = "ATTACKATONCE"
s = 4
print ("Text  : " + text)
print ("Shift : " + str(s))
print ("Cipher: " + encrypt(text,s))

# affine cypher 

def egcd(a, b):
    x,y, u,v = 0,1, 1,0
    while a != 0:
        q, r = b//a, b%a
        m, n = x-u*q, y-v*q
        b,a, x,y, u,v = a,r, u,v, m,n
    gcd = b
    return gcd, x, y
def modinv(a, m):
    gcd, x, y = egcd(a, m)
    if gcd != 1:
        return None
    else:
        return x % m
def affine_encrypt(text, key):
    return ''.join([ chr((( key[0]*(ord(t) - ord('A')) + key[1] ) % 26) 
                  + ord('A')) for t in text.upper().replace(' ', '') ])
def affine_decrypt(cipher, key):
    return ''.join([ chr((( modinv(key[0], 26)*(ord(c) - ord('A') - key[1])) 
                    % 26) + ord('A')) for c in cipher ])
def main():
    text = 'AFFINE CIPHER'
    key = [17, 20]
    affine_encrypted_text = affine_encrypt(text, key)
    print('Encrypted Text: {}'.format( affine_encrypted_text ))
    print('Decrypted Text: {}'.format
    ( affine_decrypt(affine_encrypted_text, key) ))
if __name__ == '__main__':
    main()

# Des 

def left_shift(l, r, n): 
  l = l[n:]+l[:n]
  r = r[n:]+r[:n]
  return l, r
def P8(k):
  k[0], k[1], k[2], k[3], k[4], k[5], k[6], k[7] = k[5], k[2], k[6], k[3], k[7], k[4], k[9], k[8]
  return k
while True:
  k = input("Enter Key: ")
  if len(k) == 10:
    break
#P10
k = list(k)
k[0], k[1], k[2], k[3], k[4], k[5], k[6], k[7], k[8], k[9] = k[2], k[4], k[1], k[6], k[3], k[9], k[0], k[8], k[7], k[5]
#Splitting Keys
l, r = k[0:5], k[5:10]
l, r = left_shift(l, r, 1)
k = "".join(l+r)
k = list(k)
k = P8(k)
key1 = k[:8]
print(f"Key 1: {key1}")
l, r = left_shift(l, r, 2)
k = "".join(l+r)
k = list(k)
k = P8(k)
key2 = k[:8]
print(f"Key 2: {key2}")
S0 = [[1,0,3,2],
      [3,2,1,0],
      [0,2,1,3],
      [3,1,3,2]]
S1 = [[0,1,2,3],
      [2,0,1,3],
      [3,0,1,0],
      [2,1,0,3]]
while True:
  pt = input("Enter Plain Text: ")
  if len(pt) == 8:
    break
pt = list(pt)
pt[0], pt[1], pt[2], pt[3], pt[4], pt[5], pt[6], pt[7] = pt[1], pt[5], pt[2], pt[0], pt[3], pt[7], pt[4], pt[6]
#STEP 2
def exp_perm(r):
  r = r[3:]+r[:3]+r[1:]+r[:1]
  return r
def s_box(r):
  rl, rr = r[:4], r[4:8]
  row = int(rl[0]+rl[3], 2)
  col = int(rl[1]+rl[2],2)
  s0 =  (bin(S0[row][col])[2:])
  row = int(rr[0]+rr[3], 2)
  col = int(rr[1]+rr[2],2)
  s1 = (bin(S1[row][col])[2:])
  r = list(s0+s1)
  return r
def xor(a, b):
  for i in range(len(a)):
    if a[i] == b[i]:
      a[i] = '0'
    else:
      a[i] = '1'
  return a
def step2(pt, key):
  l, r = pt[0:4], pt[4:8]
  ini_r = r
  r = exp_perm(r)
  r = xor(r, key)
  r = s_box(r)
  r[0], r[1], r[2], r[3] = r[1], r[3], r[2], r[0]
  r = xor(r, l)
  r = r+ini_r
  return r
r = step2(pt, key1)
rl, rr = r[0:4], r[4:8]
r = rr+rl
res = step2(r, key2)
res[0], res[1], res[2], res[3], res[4], res[5], res[6], res[7] = res[3], res[0], res[2], res[4], res[6], res[1], res[7], res[5]
op = "".join(res)
print(f"Cipher Text: {op}")

# Rail Fence Cypher 

def railFenceCipher(string, key):
  cipher_text = ""
  lis = []
  for i in range(key):
    lis.append([string[i]])
  dir = True
  i, row = key, key
  while(i<len(string)):
    if(row>2 or row<0):
      if(row>2):
        row-=2
      else:
        row+=2
      dir = not(dir)
    lis[row].append(string[i])
    i+=1
    if(dir):
      row+=1
    else:
      row-=1
  for i in range(key):
    j = 0
    while(j<len(lis[i])):
      cipher_text+=lis[i][j]
      j+=1
  print(cipher_text)

# columnar transposition 

import math
def encrypt(plaintext, key):
    plaintext = plaintext.replace(" ", "")
    num_columns = len(key)
    num_rows = math.ceil(len(plaintext) / num_columns)
    grid = [['' for _ in range(num_columns)] for _ in range(num_rows)]
    for i, char in enumerate(plaintext):
        row = i // num_columns
        col = i % num_columns
        grid[row][col] = char
    ciphertext = ""
    for col in key:
        col_index = key.index(col)
        for row in grid:
            ciphertext += row[col_index]
    return ciphertext
def decrypt(ciphertext, key):
    num_columns = len(key)
    num_rows = math.ceil(len(ciphertext) / num_columns)
    empty_cells = (num_columns * num_rows) - len(ciphertext)
    grid = [['' for _ in range(num_columns)] for _ in range(num_rows)]
    rows_with_extra_empty_cells = empty_cells // num_rows
    cols_with_extra_empty_cells = empty_cells % num_rows
    col_index = 0
    row_index = 0
    for char in ciphertext:
        grid[row_index][col_index] = char
        row_index += 1
        if (row_index == num_rows) or (row_index == num_rows - 1 and col_index >= num_columns - cols_with_extra_empty_cells):
            row_index = rows_with_extra_empty_cells
            col_index += 1
    plaintext = ""
    for row in grid:
        for col in key:
            col_index = key.index(col)
            plaintext += row[col_index]
    return plaintext
# Example usage
key = input("enter key:")
plaintext = input("plain text:")
ciphertext = encrypt(plaintext, key)
print("Ciphertext:", ciphertext)
decrypted_text = decrypt(ciphertext, key)
print("Decrypted text:", decrypted_text)

# DSA

p=int(input("Enter p: "))
q=0
q=int(input("Enter q: "))
H=int(input("Enter H: "))
g=int(pow(H,((p-1)/q))%p)
X=23
k=int(input("Enter k: "))
H_of_M=int(input("Enter H(M): "))
r=int((pow(g,k)%p)%q)
k_inverse=0
for a in range(1,q,1):
        k_inverse=((q*a)+1)/k
        if k_inverse.is_integer():
            break
s=int((k_inverse*(H_of_M+X*r))%q)
print()
print("Computed g is",g)
print("Computed Y is",Y)
print("Signing Components r=",r,"s=",s)
s_inverse=0
for a in range(1,q,1):
        s_inverse=((q*a)+1)/s
        if s_inverse.is_integer():
            break
w=int(s_inverse%q)
u1=(H_of_M*w)%q
u2=(r*w)%q
v=int(((pow(g,u1)*pow(Y,u2))%p)%q)
print("Computer v:",v)
print()
if v==r:
    print("-----Digitally Signed-----")
else:
    print("-----Not Digitally Signed-----")
