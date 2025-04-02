[home](../README.md)
\- [writing](README.md)

<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS_CHTML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [['$','$'], ['\\(','\\)']],
      processEscapes: true},
      jax: ["input/TeX","input/MathML","input/AsciiMath","output/CommonHTML"],
      extensions: ["tex2jax.js","mml2jax.js","asciimath2jax.js","MathMenu.js","MathZoom.js","AssistiveMML.js", "[Contrib]/a11y/accessibility-menu.js"],
      TeX: {
      extensions: ["AMSmath.js","AMSsymbols.js","noErrors.js","noUndefined.js"],
      equationNumbers: {
      autoNumber: "AMS"
      }
    }
  });
</script>

**The Right Way to Think About Machine Learning** _March 29, 2024_

The intention is that this will be a gentle start to machine learning theory.

Learning -> Take past experience, take input and use it to predict something.
We want more than memorization, we want generalization.

What is learning? A story perspective on rats vs pigeons on inductive bias, generalization, complexity, overfitting, underfitting. (10 minutes)

Introduce empirical risk minimization, i.i.d. assumption, delta confidence, eps error. PAC learning. Bias-variance tradeoff, no free lunch theorem. with Papaya example. (20 minutes)

Connect it back to ChatGPT. It has a very big hypothesis class. It uses an attention mechanism to combine information from words that are arbitrary distance away. Super huge data. Very large data, so small delta. It doesn't classify, it's generative. We want to predict sentences. There is no one correct answer. Define a distribution over sentences. There are so many different tasks and similar. OpenAI found scaling laws to show that increase in model complexity and data found predictable performance.

What assumptions are broken? i.i.d. data. May not be so. Also ChatGPT does RLHF and SFT, which is cheating. You are generating new training examples based on your model performance! Also prompt engineering. Also did bad at numbers at first, and then they just inserted a calculator into it and it did fine. An example of no free lunch. Keep adding more gadgets and gizmos.

Scraped internet. May not be i.i.d. How do you predict a distribution over text? Self-supervised learning. You take a sentence and you cut off at some point, try to predict rest of sentence. ChatGPT predicts things autoregressively. 

Why does ChatGPT do so well?
- Complex model allows it to find complex relatinoships even in this generative world.
- Stole, I mean, scraped the entire internet to train it's LLM.
- Can use prompt engineering to guide the LLM to give better responses.
- Artificial lower error with SFT
- Leverages efficiency of GPUs and many, many compute.
- So much start-up funding. Within 2 months of launching, had 100 millions customers (check fact)

So does ChatGPT have its own mind/creativity?

No! It's just learning from the data and it has a lot of data. It does really well on data-based tasks like summarizing documentation, rewriting your own essays to fit a theme, or extract key thoughts from word salads. It's not good with critical thinking or coming up with new ideas. It's not a human, so it doesn't respond to you like a human. It can't evaluate emotions. It is prompted to give neutral responses. It's goal is quite literally to please you. Rather than an AI, is more of a servant. 


