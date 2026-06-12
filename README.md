# Attention is *Not* All You Need (Dong, Cordonnier, Loukas, 2021)

##  One‑Line Summary
This paper challenges the idea that “attention alone is enough.”  
It shows that **pure self‑attention collapses** (all tokens become identical) unless you add skip connections and MLPs.

---

##  Why This Paper Matters
The original Transformer (2017) said: “Throw away recurrence and convolution — attention is all you need.”  
This follow‑up says: “Careful — if you stack attention layers without extras, the network loses expressive power *doubly exponentially* with depth.”  
In other words, attention by itself tends to make everything look the same.

---

##  Core Ideas
- **Rank Collapse:** Pure self‑attention networks converge to a rank‑1 matrix (all rows identical).  
- **Path Decomposition:** You can think of attention as many “paths” through heads across layers. Each path degenerates quickly, so stacking more layers doesn’t help.  
- **Skip Connections:** Let information bypass layers → prevents collapse.  
- **MLPs:** Add non‑linear mixing → slow down collapse, keep diversity.  
- **Layer Norm:** Mostly cosmetic — doesn’t stop collapse.

---

##  Results & Experiments
- Tested on **BERT, ALBERT, XLNet**:  
  - Remove skip connections → rapid collapse.  
  - Add skip + MLP → healthy, diverse outputs.  
- **Circle experiment:**  
  - Without skip/MLP → two circles merge into one (collapse).  
  - With skip/MLP → circles stay separate.  
- **Path length distribution (supplementary):**  
  - Real models (GPT‑3, T5, ViT, DistilBERT, MobileBERT) rely heavily on short paths.  
  - Long paths collapse faster → short paths are key to robustness.

---

##  Why It Matters
-  **Attention alone isn’t enough.**  
-  **Skip connections** are more than optimization tricks — they prevent collapse.  
-  **MLPs** add expressive power, balancing attention’s tendency toward uniformity.  
-  **Design lesson:** Transformers work because they mix attention with other components.

---

##  Key Takeaways
- Pure attention = collapse.  
- Skip connections = memory lifeline.  
- MLPs = creativity boost.  
- Layer norm = neatness, not salvation.  
- Transformers are ensembles of shallow paths, not just deep stacks.

---

##  References
- [Original Paper (ICML 2021)](https://arxiv.org/abs/2103.03404)  
- [Supplementary Material](https://arxiv.org/pdf/2103.03404.pdf)  
- [GitHub Code](https://github.com/twistedcubic/attention-rank-collapse)

---

##  Personal Note
I like how this paper “talks back” to the famous Transformer paper.  
It reminds me that bold ideas need careful checks: attention is powerful, but it needs friends (skip connections + MLPs) to stay useful.  
For me, it’s a lesson in balance — even the smartest mechanism collapses without the right support.

