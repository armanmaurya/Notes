- One type of code, which is extremely difficult to break, makes use of a large matrix to encode a message.
- The receiver of the message decodes it using the inverse of matrix.
- This first matrix, used by the sender is called the encoding matrix and its inverse is called the decoding matrix, which is used by receiver.

Message to be sent: **PREPARE TO NEGOTIATE**
And the encoding matrix be,
$$
\begin{bmatrix}
-3 & -3 & -4 \\
0 & 1 & 1 \\
4 & 3 & 4 
\end{bmatrix}
$$
We assign a number for each letter of the alphabet.
Such that A is 1, B is 2, and so on. Also we assign the number 27 to space between two words. Thus the message becomes.
$$
\begin{matrix}
P & R & E & P & A & R & E & * & T & O & * & N & E & G & O & T & I & A & T & E  \\
16 & 18 & 5 & 16 & 1 & 18 & 5 & 27 & 20 & 15 & 27 & 14 & 5 & 7 & 15 & 20 & 9 & 1 & 20 & 5
\end{matrix}
$$
## Encoding
- Since we are using 3 by 3 matrix, we break the enumerated message above into a sequence of 3 by 1 vectors.
$$
\begin{bmatrix}
16  \\
18 \\
5 \\
\end{bmatrix}
\begin{bmatrix}
16  \\
1 \\
18 \\
\end{bmatrix}
\begin{bmatrix}
5  \\
27 \\
20 \\
\end{bmatrix}
\begin{bmatrix}
15  \\
27 \\
14 \\
\end{bmatrix}
\begin{bmatrix}
5  \\
7 \\
15 \\
\end{bmatrix}
\begin{bmatrix}
20  \\
9 \\
1 \\
\end{bmatrix}
\begin{bmatrix}
20  \\
5 \\
27 \\
\end{bmatrix}
$$
- Note that it was necessary to add a space at the end of the message to complete the vector.
- We encode the message by multiplying each of the above vectors by the encoding matrix.
- We represent above vectors as columns of matrix and perform its matrix multiplication with the encoding matrix. 
$$\begin{bmatrix}
-3 & -3 & -4  \\
0  & 1  & 1  \\
4 & 3 & 4  \\
\end{bmatrix}
\begin{bmatrix}
16 & 16 & 5 & 15 & 5 & 20 & 20 \\
18 & 1 & 27 & 27 & 7 & 9 & 5 \\
5 & 18 & 20 & 14 & 15 & 1 & 27
\end{bmatrix}
$$
- We get,
$$
\begin{bmatrix}
-122 & -123 & -176  & -182 & -96 & -91 & -183 \\
23 & 19 & 47 & 41 & 22 & 10 & 32 \\
138 & 139 & 181 & 197 & 101 & 111 & 203
\end{bmatrix}
$$
- The columns of the matrix give the encoded message
- Encoding is complete
## Decoding
- To decode the message:
- The receiver writes this string as a sequence of 3 by 1 column matrices and repeats the technique using the inverse of encoding matrix.
- The inverse of this encoding matrix is the decoding matrix.
$$
\begin{bmatrix}
1 & 0 & 1 \\
4 & 4 & 3 \\
-4 & -3 & -3
\end{bmatrix}
\begin{bmatrix}
-122 & -123 & -176 & -182 & -96 & -91 & -183 \\
23 & 19 & 47 & 41 & 22 & 10 & 32 \\
138 & 139 & 181 & 197 & 101 & 111 & 203
\end{bmatrix}
$$
- Matrix obtained is
$$
\begin{bmatrix}
16 & 16 & 5 & 15 & 5 & 20 & 20 \\
18 & 1 & 27 & 27 & 7 & 9 & 5 \\
5 & 18 & 20 & 14 & 15 & 1 & 27
\end{bmatrix}
$$
The column of this matrix, written in linear form, give the original message
$$
\begin{matrix}
16 & 18 & 5 & 16 & 1 & 18 & 5 & 27 & 20 & 15 & 27 & 14 & 5 & 7 & 15 & 20 & 9 & 1 & 20 & 5  \\
P & R & E & P & A & R & E & * & T & O & * & N & E & G & O & T & I & A & T & E
\end{matrix}
$$
Message received: **PREPARE TO NEGOTIATE**