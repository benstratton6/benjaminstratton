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

## Noise in Classical Information Processing

Classical information is encoded into physical systems via a binary encoding, where the information is stored as a sequence of $\ket{0}$ and $\ket{1}$'s. The given information ones wants to encode is called the **logical information** and for $n$ bits this takes the forms of a bit-string from 
\begin{equation}
\mathfrak{B} = \{ \ket{0}, \ket{1} \}^n.
\end{equation} 

Once encoded, the logical information is either sent from one party to another, stored in a memory or processed to perform a computation. 

During these processes, the physical systems the logical information is encoded in will interact with the environment. This can have the effect of alternating the encoded logical information. Namely, **bit-flips** can occur, where an encoded $\ket{0}$ is flipped to a $\ket{1}$ or a $\ket{1}$ is flipped to a $\ket{0}$. This error can be modelled by the Pauli $X$ operator as
\begin{equation}
X \ket{0} = \ket{1}, ~~ X \ket{1} = \ket{0}, ~ ~ {\rm where} ~ ~X = \ket{0}\bra{1} + \ket{1}\bra{0}.
\end{equation}

After the information has been sent or stored in memory for some time, it needs to be decoded. In the absence of any noise, the decoded information will be the same as the encoded information. However, when noise occurs the information can be changed, leading to the incorrect information being decoded. Similarly, when performing a computation in the absence of noise, the correct output of the computation for the given input will be decoded. However, if noise has occurred during the computation, the incorrect output for the given input may be decoded. 

## Classical Error Correction

Error correction aims to combat noise through redundancy — each logical bit is instead encoded in many physical bits. A method of encoding logical information through redundancy in order to protect against errors is known as an **error correcting code**. 

<!-- Whilst physical error rates are low when storing classical information, it is still necessary to employ error correction in scenarios such as deep space communication where the large distance between the sender and receiver leads to more physical errors occurring.  -->

### Error Detection 

When an error occurs on the physical bits an error correcting code aims to:

1. identify that an error has occurred, 
2. if so, identify where the error has occurred (to which bits), 
3. correct the error. 

Typically, steps (1) and (2) occur at the same time. A measurement in made on the physical bits with the ouput of the measurement (known as a **syndrome**) detailing both that an error has occurred and where that error has occurred. In some codes, step (2) may not be necessary to fulfil step (3), with the error being correctable without its exact location (on exactly which bit is has occurred) being known.

On the other hand, some codes are able to fulfill (1) without being able to fulfill (2) or (3). Such codes are said to perform **error detection**. In these cases, it is known that an error has occurred, but it is not know how to correct it. 

With only the use of error detection, one can ensure the correct performance of some information processing protocol in the presence of noise by just repeat the protocol until it happens error free, discarding any cases where an error is detected and starting again. Although, depending on the probability of an error occurring, this might be very inefficient. 

### The Repetition Code

The simplest classical error correcting code is the 3-bit repetition code. Here, each bit of logical information is encoded via three physical bits of information. Specifically,
\begin{equation}
\ket{0}_{L} \rightarrow \ket{000}, ~~~ \ket{1}_L \rightarrow \ket{111}, 
\end{equation}
where the left side of the arrow is a bit of logical information, denoted by the subscript $L$, and the right hand side is the physical information. The bit-string of logical information $\ket{010}_L$ is therefore physically encoded as $\ket{000111000}$, where 9 physical bits have been used to encode 3 logical bits. The bit-string $\ket{000}$ and $\ket{111}$ are called **logical codewords** of this error correcting code. 

Consider a logical bit, say $\ket{0}$, is sent from one party to another via a noisy channel that causes the first physical bit to be flipped,
\begin{equation}
\ket{0}_L = \ket{000} \xrightarrow{\rm Noisy~ Channel} (X \otimes \mathbb{I} \otimes \mathbb{I}) \ket{000} = \ket{100}.
\end{equation}

Upon receiving the three physical bits, a **majority vote** can be used to identify if any errors have occurred. The three bits are read-out (measured) and the number of $\ket{0}$ and $\ket{1}$'s are counted. If there are more $\ket{0}$'s than $\ket{1}$'s then the logical information is decoded as $\ket{0}_L$ and vice versa. In the above example, there are two $\ket{0}$'s and one $\ket{1}$, so $\ket{0}_L$ is decoded. 

The 3 bit repetition code fails if a bit-flip (X) error occurs on more then one physical bit. For example, consider the following error on two physical bits, 
\begin{equation}
\ket{0}_L = \ket{000} \xrightarrow{\rm Noisy~ Channel} (X \otimes X \otimes \mathbb{I}) \ket{000} = \ket{110}.
\end{equation}
A majority vote will count one $\ket{0}$ and two $\ket{1}$'s, leading to $\ket{1}_L$ being decoded. A logical error will therefore have occurred, meaning an error has been applied to the logical information. 

If an error occurs on three physical bits then 
\begin{equation}
\ket{0}_L = \ket{000} \xrightarrow{\rm Noisy~ Channel} (X \otimes X \otimes X) \ket{000} = \ket{111},
\end{equation}
meaning the $\ket{0}_L = \ket{000}$ codeword is flipped to the $\ket{1}_L=\ket{111}$ codeword. A majority vote will therefore decode $\ket{1}_L$, meaning a logical error will have occurred whilst believing that no physical error has occurred. 

The repetition code is therefore able to detect and then correct errors if the noisy channel consists of only a single bit flip. It is only able to detect errors if the noisy channel consists of one or two bits flip. Hence, for singular errors, the  repetition code is an error correcting code, whilst for one or two errors it is an error detecting code.  

### Code Distance

This distance of a code is the minimum numbers of errors that will change one codeword to another. Alternatively, the distance of a code is the minimum number of errors that will go undetected. 

In the example of the repetition code, three physical errors take one code word to the other, meaning the distance of the code is three. Alternatively, it is when three physical errors occur that one does not even know an error has occurred, again leading to the conclusion that the code distance is three. 

There exists the following relationship between code distance, $d$, and correctable errors, t, 
\begin{equation}
d = 2t + 1.
\end{equation}

### Labelling Codes

Codes are labelled as $[n, k, d]$, where $n$ is the number of physical bits, $k$ is the number of logical bits and $d$ is the code distance.


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
