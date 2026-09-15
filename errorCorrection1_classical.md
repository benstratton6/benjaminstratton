---
title: Classical Error Correction 
subject: Tutorial
# subtitle: The space in which quantum states live
# short_title: How to MyST
authors:
  - name: Benjamin Stratton
    # affiliations:
    #   - Executable Books
    #   - Curvenote
    orcid: 0009-0001-2746-3668
    email: ben.stratton@bristol.ac.uk
# license: CC-BY-4.0
keywords: bits, bit-flips, repetition code 
abstract: A brief overview of the terminology of error correction, including an example of the simplest forms of classical error correction - the repetition codes, and details on why different error correcting codes are needed in the quantum case. 
exports:
#   - format: docx
  - format: pdf
    template: physical_review_journals
    article_type: Report
---

All information is encoded in physical systems. These physical systems are subject to noise - unwanted interactions with the environment - that can corrupt this encoded information. The goal of error correction is to combat this noise and hence ensure that the encoded information is correctly decoded. 

The following resources were used in the process of writing this collection of notes on error correction: 
- [Stabilizer Codes and Quantum Error Correction](
https://doi.org/10.48550/arXiv.quant-ph/9705052)
- [Quantum Error Correction: An Introductory Guide](
https://doi.org/10.1080/00107514.2019.1667078)
- [Surface codes: Towards practical large-scale quantum computation](
https://doi.org/10.1103/PhysRevA.86.032324)
- [Quantum Error Correction, Prof. Kastoryano](https://www.thp.uni-koeln.de/kastoryano/ExSheets/Notes_v7.pdf)
- Lectures On Computation, Feynman, R.P.
- [Quantum error correction and fault tolerance: A comprehensive tutorial](https://doi.org/10.48550/arXiv.2605.29137)
- [Blog by Arthur Pesah](https://arthurpesah.me/)
- [But what are Hamming codes? The origin of error correction](https://www.youtube.com/watch?v=X8jsijhllIA)

## Noise in Classical Information Processing

Classical information is (most often) encoded into physical systems via a binary encoding, where the information is stored as a sequence of $\ket{0}$ and $\ket{1}$'s. The given information ones wants to encode is called the **logical information** and for $k$ bits this takes the forms of a bit-string from 
\begin{equation}
\mathfrak{B} = \{ \ket{0}, \ket{1} \}^k.
\end{equation} 

Once encoded, the logical information is either sent from one party to another, stored in a memory or processed to perform a computation. 

During these processes, the physical systems the logical information is encoded in will interact with the environment. This can have the effect of alternating the encoded logical information. Namely, **bit-flips** can occur, where an encoded $\ket{0}$ is flipped to a $\ket{1}$ or a $\ket{1}$ is flipped to a $\ket{0}$. This error can be modelled by the Pauli $X$ operator as
\begin{equation}
X \ket{0} = \ket{1}, ~~ X \ket{1} = \ket{0}, ~ ~ {\rm where} ~ ~X = \ket{0}\bra{1} + \ket{1}\bra{0}.
\end{equation}

After the information has been sent or stored in memory for some time, it needs to be decoded. In the absence of any noise, the decoded information will be the same as the encoded information. However, when noise occurs the information can be changed, leading to the incorrect information being decoded. Similarly, when performing a computation in the absence of noise, the correct output of the computation for the given input will be decoded. However, if noise has occurred during the computation, the incorrect output for the given input may be decoded. 

## Classical Error Correction

Error correction aims to combat noise through redundancy, meaning additional physical are used to protect against errors. For example, $n$ physical bits are used to encode $k$ logical bits, where $k < n$. Any method of encoding logical information through redundancy in order to protect against errors is known as an **error correcting code**. 

### Error Detection 

When an error occurs on the physical bits an error correcting code aims to:

1. identify that an error has occurred, 
2. if so, identify where the error has occurred (to which bits), 
3. correct the error. 

Typically, steps (1) and (2) occur at the same time. A measurement is made on the physical bits with the ouput of the measurement (known as a **syndrome**) detailing both that an error has occurred and where that error has occurred. In some codes, step (2) may not be necessary to fulfil step (3), with the error being correctable without its exact location (on exactly which bit is has occurred) being known.

On the other hand, some codes are able to fulfill (1) without being able to fulfill (2) or (3). Such codes are said to perform **error detection**. In these cases, it is known that an error has occurred, but it is not known how to correct it. 

With only the use of error detection, one can ensure the correct performance of some information processing protocol in the presence of noise by just repeat the protocol until it happens error free, discarding any cases where an error is detected and starting again. Although, depending on the probability of an error occurring, this might be very inefficient. 
(classical_error_correction_page)=
### The Repetition Code

A simple example of a classical error correcting code is the 3-bit repetition code. Here, each bit of logical information is encoded via three physical bits of information. Specifically,
\begin{equation}
\ket{0}_{L} \rightarrow \ket{000}, ~~~ \ket{1}_L \rightarrow \ket{111}, 
\end{equation}
where the left side of the arrow is a bit of logical information, denoted by the subscript $L$, and the right hand side is the physical information. The bit-string of logical information $\ket{010}_L$ is therefore physically encoded as $\ket{000111000}$, where 9 physical bits have been used to encode 3 logical bits. The bit-string $\ket{000}$ and $\ket{111}$ are called **logical codewords** of this error correcting code, and they are the physical bit-strings used to encode the logical bit-strings.  

Consider now that a logical bit $\ket{0}$ is sent from one party to another via a noisy channel that causes the first physical bit to be flipped,
\begin{equation}
\ket{0}_L = \ket{000} \xrightarrow{\rm Noisy~ Channel} (X \otimes \mathbb{I} \otimes \mathbb{I}) \ket{000} = \ket{100}.
\end{equation}

Upon receiving the three physical bits, a **majority vote** can be used to identify if any errors have occurred. The three bits are read-out (measured) and the number of $\ket{0}$ and $\ket{1}$'s are counted. If there are more $\ket{0}$'s than $\ket{1}$'s then the logical information is decoded as $\ket{0}_L$ and vice versa. In the above example, there are two $\ket{0}$'s and one $\ket{1}$, so $\ket{0}_L$ is decoded. 

The 3 bit repetition code fails if a bit-flip (X) error occurs on more then one physical bit. For example, consider the following error on two physical bits, 
\begin{equation}
\ket{0}_L = \ket{000} \xrightarrow{\rm Noisy~ Channel} (X \otimes X \otimes \mathbb{I}) \ket{000} = \ket{110}.
\end{equation}
A majority vote will count one $\ket{0}$ and two $\ket{1}$'s, leading to $\ket{1}_L$ being decoded. A logical error will therefore have occurred, meaning an error has been applied to the logical information, in this case changing $\ket{0}_L$ to $\ket{1}_L$.

If an error occurs on three physical bits then 
\begin{equation}
\ket{0}_L = \ket{000} \xrightarrow{\rm Noisy~ Channel} (X \otimes X \otimes X) \ket{000} = \ket{111},
\end{equation}
meaning the $\ket{0}_L = \ket{000}$ codeword is flipped to the $\ket{1}_L=\ket{111}$ codeword. A majority vote will therefore decode $\ket{1}_L$, meaning a logical error will have occurred whilst believing that no physical error has occurred. 

The repetition code is therefore able to detect and then correct errors if the noisy channel consists of only a single bit flip. It is only able to detect errors if the noisy channel consists of one or two bits flip, but if two bit-flips occur it will decode the error incorrectly. Hence, for singular errors, the repetition code is an error correcting code, whilst for one or two errors it is an error detecting code.  

### Code Distance

This distance of a code is the minimum numbers of errors that will change one codeword to another. Alternatively, the distance of a code is the minimum number of errors that will go undetected. 

In the example of the repetition code, three physical errors take one code word to the other, meaning the distance of the code is three. Alternatively, it is when three physical errors occur that one does not even know an error has occurred, again leading to the conclusion that the code distance is three. 

There exists the following relationship between code distance, $d$, and correctable errors, t, 
\begin{equation}
d = 2t + 1.
\end{equation}

### Labelling Codes

Codes are labelled as $[n, k, d]$, where $n$ is the number of physical bits, $k$ is the number of logical bits and $d$ is the code distance.

The rate, $R$, of an error correcting code is then the ratio of the logical bits to the physical bits
\begin{equation}
R = \frac{k}{n}.
\end{equation}

(section_parity_check_codes_target)=
### Parity Check Codes

Here, we introduce the notion of parity checks and give some examples of how they can be used in classical error correcting codes. 

```{card} 
:header: **Parity**

Given an $n$ bit-string $\vert \bm{a} \rangle = \vert a_1 a_2 \ldots a_n \rangle \in \mathfrak{B}$, the parity of the string, $p(\bm{a})$, is given by 
\begin{equation}
p(\bm{a}) = a_1 \oplus a_2 \oplus \ldots \oplus a_n,
\end{equation}
where $\oplus$ is addition modulo $2$. The parity therefore determines if the number of $1$'s in the bit-string is even or odd, where  
\begin{equation}
p(\bm{a}) = \begin{cases}
0 \rightarrow ~\bm{a}{\rm~has~ an~ even~number~of~}1's \\
1 \rightarrow ~\bm{a}{\rm~has~ an~ odd~number~of~}1's
\end{cases}
\end{equation}

```
(error_detection_with_parity_example)=
***Error Detection With Parity***

We now demonstrate an error detecting code where $k=3$ logical bits are stored in $n=4$ physical bits, with the redundant $4$th bit storing the parity of the logical bits. 

For a $3$ bit-string $\ket{\bm{a}}=\ket{a_1a_2a_3}$, the encoding of this error correcting code is therefore 
\begin{equation}
\ket{a_1a_2a_3} \xrightarrow{\rm Encoding} \ket{a_1a_2a_3, p(\bm{a})}.
\end{equation}  

Now, consider that the encoded state is sent from one party to another and a bit-flip error occurs on the first bit, 
\begin{equation}
\ket{a_1a_2a_3, p(\bm{a})} \xrightarrow{\rm Noisy~ Channel} \ket{(a_1 \oplus 1)a_2a_3, p(\bm{a})}.
\end{equation}
Upon receiving the encoded state, the first three bits can be measured and their parity calculated. Then, the final bit can be measured and compared to the calculated parity value. 

If the parities match, then the receiving party will know that either no error or two errors will have occurred, as 
\begin{equation}
p(\bm{a}) = p(\bm{a}) \oplus 1 \oplus 1.
\end{equation}
If the parties do not match, then they will know either one or three errors will have occurred, as 
\begin{equation}
p(\bm{a}) \oplus 1 = p(\bm{a}) \oplus 1 \oplus 1 \oplus 1.
\end{equation}
Note, we have assumed no error has occurred on the parity bit. 

More concretely, if the receiving party has the state $\ket{\bm{b}} = \ket{b_1b_2b_3p(\bm{a})}$, where $\bm{b}$ is an unknown $3$ bit-string, then they can then calculate 
\begin{equation}
s = b_1 \oplus b_2 \oplus b_3 \oplus p(\bm{a}),
\end{equation} 
where $s$ is the syndrome of this code. From this, they can concluded  
\begin{equation}
s = \begin{cases}
0 \rightarrow {\rm~zero~or~two~errors~occurred} \\
1 \rightarrow {\rm~one~or~three~errors~occurred}
\end{cases}
\end{equation} 
Note, if it is assumed that most one error has occurred, including on the parity bit, then a $s=1$ syndrome will mean an error could have occurred on any of the $4$ physical bits. 

This code is an example of an error detecting code, as, even if we assume only one bit flip error has occurred, it is still not known _where_ that error has occurred i.e., to which bit. This examples does, however, demonstrate that parity checks are a powerful method for determining if bit-flip errors have occurred. 

:::{dropdown} Code Words: Error Detection With Parity

\begin{align*}
&\ket{000}_L \rightarrow \ket{0000} \\
&\ket{001}_L \rightarrow \ket{0011} \\
&\ket{010}_L \rightarrow \ket{0101} \\
&\ket{011}_L \rightarrow \ket{0110} \\
&\ket{100}_L \rightarrow \ket{1001} \\
&\ket{101}_L \rightarrow \ket{1010} \\
&\ket{110}_L \rightarrow \ket{1100} \\
&\ket{111}_L \rightarrow \ket{1111} \\
\end{align*}

:::

(error_correction_with_parity_example)=
***Error Correction With Parity***

We now give an example of where parity checks can be used to create an error correcting code. Interestingly, we will see that there is enough freedom to also error correct the parity bits if we assume at most one bit-flip occurred. 

The code stores $k=3$ logical bits in $n=6$ physical bits as
\begin{equation}
\ket{a_1a_2a_3} \xrightarrow{\rm Encoding} \ket{a_1a_2a_3, p_1 p_2 p_3},
\end{equation}  
where 
\begin{equation}
p_1 = a_1 \oplus a_2, ~ ~ p_2 = a_1 \oplus a_3, ~ ~ p_3 = a_2 \oplus a_3.
\end{equation}
Now, if the receiving party gets the state $\ket{b_1b_2b_3, p_1'p_2'p_3'}$, where all bits are unknown, then they can then calculate the following syndromes 
\begin{align*}
s_1 &= b_1 \oplus b_2 \oplus p_1' \\
s_2 &= b_1 \oplus b_3 \oplus p_2' \\
s_3 &= b_2 \oplus b_3 \oplus p_3' \\
\end{align*}
It can now be verified through a quick calculation that, if it is assumed that at most one bit-flip error occurred, that there is enough combinations of syndromes to both detect and locate an error. Specifically, it is known that 
(error_syndromes_of_parity_error_correction)=
\begin{align*}
(s_1, s_2, s_3) &\longrightarrow ~{\rm Bit ~Flipped} \\
(0,0,0) &\longrightarrow ~{\rm None} \\
(0,0,1) &\longrightarrow ~ p_3 \\
(0,1,0) &\longrightarrow ~ p_2 \\
(0,1,1) &\longrightarrow ~ a_3 \\
(1,0,0) &\longrightarrow ~ p_1 \\
(1,0,1) &\longrightarrow ~ a_2 \\
(1,1,0) &\longrightarrow ~ a_1 \\
\end{align*}
:::{dropdown} Proof

As an example, assume that a bit-flip occurs on the first bit
\begin{equation}
\ket{a_1a_2a_3, p_1 p_2 p_3} \xrightarrow{\rm Noisy~ Channel} \ket{(a_1 \oplus 1)a_2a_3, p_1 p_2 p_3}.
\end{equation}
The output syndromes will therefore be 
\begin{align*}
s_1 &= (a_1 \oplus 1) \oplus a_2 \oplus p_1 = 1 \\
s_2 &= (a_1 \oplus 1) \oplus a_3 \oplus p_2 = 1 \\
s_3 &= a_2 \oplus a_3 \oplus p_3 = 0 \\
\end{align*}

If, instead, an error occurs on the third parity bit
\begin{equation}
\ket{a_1a_2a_3, p_1 p_2 p_3} \xrightarrow{\rm Noisy~ Channel} \ket{a_1a_2a_3, p_1 p_2 (p_3 \oplus 1)},
\end{equation}
then the output syndromes will be 
\begin{align*}
s_1 &= a_1 \oplus a_2 \oplus p_1 = 0 \\
s_2 &= a_1 \oplus a_3 \oplus p_2 = 0 \\
s_3 &= a_2 \oplus a_3 \oplus (p_3 \oplus 1) = 1 \\
\end{align*}
:::
To correct the error, one needs to check the syndrome in the table and then flip the corresponding bit. 

:::{dropdown} Code Words: Error Correction With Parity

\begin{align*}
&\ket{000}_L \rightarrow \ket{000,000} \\
&\ket{001}_L \rightarrow \ket{001,011} \\
&\ket{010}_L \rightarrow \ket{010,101} \\
&\ket{011}_L \rightarrow \ket{011,110} \\
&\ket{100}_L \rightarrow \ket{100,110} \\
&\ket{101}_L \rightarrow \ket{101,101} \\
&\ket{110}_L \rightarrow \ket{110,011} \\
&\ket{111}_L \rightarrow \ket{111,000} \\
\end{align*}

:::

In the next page, we will review the mathematical formulation of a broad class of quantum error correcting codes called linear codes. Firstly, however, we will argue why there is need to extend error correction to the quantum domain. 

## The Need for Quantum Error Correction

There exists the need for new error correcting codes when considering quantum systems as the previously discovered classical codes are not sufficient for the following reasons:

1. **Quantum states experience errors beyond bit flips**: 

    Whilst bits can take only one of two     values, $\ket{0}$ or $\ket{1}$, qubits can be in any state of the form 

    \begin{equation}
    \ket{\psi} = \alpha \ket{0} + \beta \ket{1} : \alpha, \beta~\in~\mathbb{C}^1, ~ ~ \vert \alpha \vert^2 + \vert \beta \vert^2 = 1.
    \end{equation}

    Hence, qubits form a continuous set, rather then a discrete set like classical bits. This means errors beyond just bit-flips ($X$ errors) can occur. Specifically, an infinite number of potential errors could occur if $ \alpha $ and $ \beta $ are changed by any amount. Fortunately, however, errors on quantum states can be digitised, with only phase errors needing to be considered in addition to bit-flip errors. The phase error is modelled by the Pauli-$Z$ operator
    \begin{equation}
    Z \ket{0} = \ket{0}, ~ ~ Z \ket{1} = - \ket{1}, ~~ {\rm where} ~  Z = \ket{0} \bra{0} - \ket{1} \bra{1},
    \end{equation}
    which acts on the qubit state as 
    \begin{equation}
    \ket{\psi}  \xrightarrow{\rm Phase~Error} Z \ket{\psi} = \alpha \ket{0} - \beta \ket{1}.
    \end{equation}

    :::{dropdown} Proof 
    
    
    Firstly, note that an error applied to a qubit is just some unitary operator, $U$. (Note, this is not true if the error is some channel). 
    
    Given that the set of operators $\{ \mathbb{I}, X, Y, Z \}$ form an operator basis for all $2 \times 2$ complex matrices, there exists complex numbers $\alpha, \beta, \gamma, \delta$ such that 
    \begin{equation}
    U = \alpha \mathbb{I} + \beta X + \gamma Y + \delta Z. 
    \end{equation}
    Furthermore, given that $Y=iXZ$, $U$ can be written as
    \begin{equation}
    U = \alpha \mathbb{I} + \beta X + \tilde{\gamma} XZ + \delta Z, 
    \end{equation}
    where $\tilde{\gamma} = i \gamma$ is just some other complex number. 

    The error $U$ applied to $\ket{\psi}$ is then 
    \begin{align*}
    U \ket{\psi} &= \big( \alpha \mathbb{I} + \beta X + \tilde{\gamma} XZ + \delta Z \big) \ket{\psi}, \\
    &= \alpha \mathbb{I} \ket{\psi} + \beta X \ket{\psi}+ \tilde{\gamma} XZ \ket{\psi} + \delta Z \ket{\psi}.
    \end{align*}

    Hence, all errors applied to qubits are some combination of $X$ and $Z$ errors. 
    
    Error correction then involves a projective measurement step, meaning that for any error $U$, once measured the error that will have occurred with be either an $X$ error, $Z$ error or both in succession.

    Any quantum error correcting protocol involving qubits therefore needs only to be able to identify and correct $X$ and $Z$ errors. 

    :::

2. **The No Cloning Theorem prevents protection through repetition**: 

    There exists no universal quantum cloner, meaning there exists no operation that can take as an input some arbitrary quantum state $\ket{\psi}$ and return as an output $\ket{\psi} \otimes \ket{\psi}$. Classical error correction makes use of the fact that information can be duplicated at will. The no-cloning theorem prevents this being possible in quantum error correction. 

3. **Measurements can irreversible alter quantum states**:

    As seen above in the repetition code, classical information can be measured and the value of a bit found without the stored information being altered. This means that given a bit $\ket{0}$, a measurement can be made which tells some agent that the bit is $\ket{0}$ without the bit being changing from being a $\ket{0}$. This measurement can be made as many times as one likes without the information being altered. This is not the case with quantum information, where in general measurement will irreversible alter the state and hence the encoded information. 
