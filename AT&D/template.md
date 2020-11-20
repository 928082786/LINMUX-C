
<font size=6 color=gray> (Title) </font>

# Adversarial Examples Are Not Easily Detected: Bypassing Ten Detection Methods

<font size=6 color=gray> (Contributions) </font>

We make the following contributions:
1. We find that many defenses are unable to detect adversarial examples, even when the attacker is oblivious to the specific defense used.
2. We break all existing detection methods in the white-box (and black-box) setting by showing how to pick good attackerloss functions for each defense.
3. We draw conclusions about the space of adversarial examples, and offer a note of caution about evaluating solely on MNIST; it appears that MNIST has somewhat different security properties than CIFAR.
4. We provide recommendations for evaluating defenses.
---
> The author always claimed that FGSM and JSMA is too weak to evaluation whether a detection method is better.

>Why?

>Answer : We re-implement these two <font color=DeepSkyBlue >defenses </font> and find that adversarial retraining is able to detect adversarial examples when generated with the fast gradient sign and JSMA attacks with near-100% accuracy.
<font color=DeepSkyBlue >
> - *On the (Statistical) Detection of Adversarial Examples.
arXiv preprint arXiv:1702.06280 (2017).*
> - *Adversarial and Clean Data
Are Not Twins. arXiv preprint arXiv:1704.04960 (2017).*
</font>

---
<font size=6 color=gray> (Ready work) </font>


### <font color=IndianRed> Three attack methods</font>

1. A strong attack (Zero-Knowledge):
2. An adaptive, white-box attack (Perfect-Knowledge)
3. A black-box attack (Limited-Knowledge):

### <font color=IndianRed> Attack method </font>
- C&W method

### <font color=IndianRed> Defence methods </font>

> - <font color=HotPink>Grosse</font> *On the (Statistical) Detection of Adversarial Examples.
arXiv preprint arXiv:1702.06280 (2017).*
> - <font color=HotPink>Gong</font> *Adversarial and Clean Data
Are Not Twins. arXiv preprint arXiv:1704.04960 (2017).*
> - <font color=HotPink>Metzen</font> *On Detecting Adversarial Perturbations. In International Conference on Learning Representations. arXiv preprint arXiv:1702.04267.*
> - <font color=HotPink>Hendrycks</font> *Early Methods for Detecting Adversarial
Images. In International Conference on Learning Representations*
> - <font color=HotPink>Bhagoji,</font> *Dimensionality Reduction as a Defense against Evasion Attacks on Machine Learning Classifiers. arXiv preprint arXiv:1704:02654 (2017)*

---
<font size=6 color=gray> (Show work) </font>


## <font color=IndianRed>Zero-Knowledge</font>

- <font color=Plum>Grosse and Gong methods</font>
  
    <font color=HotPink>Grosse and Gong methods </font>perform well on MNIST, but not on CIFAR10. 
- <font color=Plum>Metzen method</font>

    High false positive rate on <font 
    color=HotPink>Metzen method</font> 

- <font color=Plum>Hendrycks method</font>

    As for <font color=HotPink>Hendrycks</font> claimed(Input Image PCA), there is no difference on the first principal components, but there is a substantial
    difference between natural and adversarial instances on the later components.

    ![](./PCA_input.png)

    This method seems perfect, however, the reason is because of MNIST itself. ***the detected difference between the natural and adversarial
    examples is because the border pixels are nearly always zero
    for natural MNIST instances, whereas typical adversarial examples
    have non-zero values on the border.***


## <font color=IndianRed>Perfect-Knowledge</font>

- <font color=Plum>Grosse method</font>
  
  Use C&W directly(less distortion)

- <font color=Plum> Gong method </font>
  
  Define a function 
    $$
    G(x)_{i} = \left\{
        \begin{aligned}  
        Z_{F}(x)_{i} & &i <=N \\
        (Z_{D}+1)*max_{j}Z_{F}(x)_{j} & &i=N+1        \end{aligned}
        \right.
    $$
    Now we treat this function G as if it were a neural network, and
    feed it directly into C&W’s attack algorithm instead of the function
    Z. It is easy to see that if an instance $x ′$ is classified by $G$ as label
    $l ≤ N$ then both $C(x ′) = l$ and the detector classifies $x ′$ as natural
    (non-adversarial). This approach successfully generates adversarial
    examples against Gong’s defense with 100% success.

- <font color=Plum> Metzen method </font>
  
    Generate adversarial examples
    using C&W’s attack applied to the same function $G(·)$ defined in <font color=HotPink>Gong</font>

- <font color=Plum>Hendrycks method</font>
    
    We can generate adversarial examples that are restricted to
change only the first k principal components and these adversarial examples that are not detected by the Hendrycks defense.

## <font color=IndianRed>Limited-Knowledge</font>

Split the training set in half. First half is known to the attacker and the second half is used by the defender to train their network. Then apply the C&W attack to each instance in the test set to generate adversarial examples for $R_{1}$ (model trained on first half dataset), and we test whether they fool $R_{2}$ (the other half one).

> **In fact this is transfering attacking**

---
<font size=6 color=gray> (Conclusion) </font>
