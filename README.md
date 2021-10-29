# Quantum Image Distortions - Princeton Qiskit Fall Fest Hackathon 2020
## Project Motivation:
“A growing number of quantum computing algorithms with potential or (in some cases) proven applications in several branches of science and technology have been suggested. One such area to have emerged into the spotlight is the new field of quantum image processing (QIP), which seeks to extend traditional image processing and its applications to (or using) quantum computing” [5].
Because quantum computation has properties, notably entanglement and parallelism, it is hoped that QIP will surpass its traditional counterpart, through “computing speed, security, and minimum storage requirements” [5].

Images are encrypted for many reasons, including “identifying the creator of an image, protecting copyright information, deterring piracy, and blocking images from being viewed by users who shouldn't have access to them” [4]. By encrypting images, you can send them without worrying about external interception of the information in the image.

Because we are applying quantum gates between encoding and decoding an image (and, in some of the transformations, utilizing Quantum Fourier Transform and Inverse Quantum Fourier Transform), it is similar to a simplified image encryption algorithm. One of the most recent image encryption algorithm developed in quantum space similarly has a quantum random-phase gate and utilizes a type of Fourier transform called Hadamard transform in the paper “Quantum Image Encryption Algorithm Based on Image Correlation Decomposition" [6].


## Project Description:
1. Image Preparation (Changing the Resolution, Cropping, Centering)

Using Grayscale → Cropping the Image to a Square → Reducing Resolution to 32 x 32 pixels.

2. FRQI Method Encoding using an Ancillary Qubit

Multiple Methods to go about Encoding Images:
Qiskit Textbook: Flexible Representation of Quantum Images (FRQI) or  Novel Enhanced Quantum Representation (NEQR).
Multi Channel Representation for Quantum Images (MCQI) for better RBG representation.
FRQI: Encoding an image of size m = n x n (pixels) into log2(m) qubits. Drawback: m gates to perform the encoding of such an image. More info: https://qiskit.org/textbook/ch-applications/image-processing-frqi-neqr.html 

3. The Distortions:

TRANSFORMATION 1: QFT(Quantum Fourier Transform), A more efficient discrete fourier transform quantum algorithm, can be used as part of many other more complex image processing techniques.

TRANSFORMATION 2: Rotation in Frequency Space, A simple transformation that runs the QFT then rotates all the Qubits slightly, produces what looks like noise but should be decryptable if you know what the original rotation was. 

TRANSFORMATION 3: Rotate each Qubit by a random angle, similarly this works like an encryption algorithm but doesn’t happen in frequency space. The qubits should be decryptable if you know the angles that were used to encrypt, but once it is measured without decryption the image just looks like noise and the data is lost.

TRANSFORMATION 4: Uniform Rotation, similar to the last transformation but all the qubits are rotated the same amount.

DECRYPTION 1: The inverse of the QFT (QFT†) also known as Quantum Phase Estimation.

DECRYPTION 3: Decodes the qubits from Transformation 3, reversing the random rotations applied. 

## Limitations and Possible Extensions:
Limitations:
At least 5 minutes of run-time for measuring and decoding an image was observed, which caused us to scrap many ideas along the way because we couldn’t see the end product.
The limited number of qubits we can simulate limits the size of the images we can use to 32x32.
Aer_qasm_simulator backend limitations, requires memory.
IBM Q and such paid backends allowing for more precision in calculation of distortions.

Extensions:
Quantum Edge Detection
Merging Images, High Pass, Low Pass Filters Applied
RBG Color MCQI Method can be utilized with larger memory.

## Citations:
Our encoding and decoding function relies on the FRQI (Flexible Representation of Quantum Images) method whose fundamentals can be found in the IBM Qiskit Textbook: https://qiskit.org/textbook/ch-applications/image-processing-frqi-neqr.html.


The FRQI package that was utilized to use said method can be found in user Paritosh Chauhan's Github: https://github.com/paritoshkc/Quantum-Computing/blob/master/frqi.py and in user Shedka's Github: https://github.com/Shedka/citiesatnight/blob/master/frqi.py.


References:
<a id="1">[1]</a>
Yan F, Iliyasu AM, Jiang Z. Quantum Computation-Based Image Representation, Processing Operations and Their Applications. Entropy. 2014; 16(10):5290-5338. https://doi.org/10.3390/e16105290
<a id="2">[2]</a>
Sun, Bo & Iliyasu, Abdullah & Yan, Fei & Dong, Fangyan & Hirota, Kaoru. (2013). An RGB Multi-Channel Representation for Images on Quantum Computers. Journal of Advanced Computational Intelligence and Intelligent Informatics. 17. 404-417
<a id="3">[3]</a>
https://link.springer.com/content/pdf/10.1007%2F978-981-32-9331-1.pdf
<a id="4">[4]</a>
Smith, Nicholas. “Why Don't Pictures Sent to My Email Come through?” Chron.com, Chron.com, 21 Nov. 2017, https://smallbusiness.chron.com/dont-pictures-sent-email-come-through-64195.html. 
<a id="5">[5]</a>
Bennett, C., DiVincenzo, D. Quantum information and computation. Nature 404, 247–255 (2000). https://doi.org/10.1038/35005001
<a id="6">[6]</a>
Hua, Tianxiang and Chen, Jiamin and Pei, Dongju and Zhang, Wenquan and Zhou, Nanrun, “Quantum Image Encryption Algorithm Based on Image Correlation Decomposition", International Journal of Theoretical Physics, February 2015, doi: 10.1007/s10773-014-2245-z, https://ui.adsabs.harvard.edu/abs/2015IJTP...54..526H 
<a id="7">[7]</a>
Team, The Qiskit. “Quantum Fourier Transform.” Qiskit, IBM, 18 Oct. 2021, https://qiskit.org/textbook/ch-algorithms/quantum-fourier-transform.html. 
<a id="8">[8]</a>
Team, The Qiskit. “Quantum Image Processing - FRQI and NEQR Image Representations.” Quantum Image Processing - FRQI and NEQR Image Representations, IBM, 18 Oct. 2021, https://qiskit.org/textbook/ch-applications/image-processing-frqi-neqr.html. 
