Question: **is the recent warming real, or could it just be random luck in which years got measured?**

→ Compares two chunks of German temperature data (1881–1950 vs. 1990–2025) (means p. annua)

→ recent period is 1.39°C warmer (means difference)

**Bootstrap CI — "what if I reshuffled?"** 

We can’t get different data since we can’t go back in time but: we can average the difference across different subsets of the same data - 10,000 times. 

Then I have 10,000 simulated "what could the gap have looked like by chance" values. The middle 95% of those is my confidence interval: 

**\[1.10, 1.67\]**. 

Since 0 isn't anywhere in that range → "no difference" isn't a plausible outcome of random luck.

**Welch t-test —**

Same but without simulating. 

"Welch" just means it doesn't assume both periods vary by the same amount . 

It agrees: p ≈ 4e-13 → a gap this big (1.39) would be impossibly rare if there were truly no difference.

**Cohen's d — how big is "big"?**

1.39°C alone doesn't tell you if that's a huge or trivial gap — it depends on how much temperatures naturally vary year to year. Cohen's d rescales the gap into units of that natural variation. d = 1.97 means the two jars are nearly 2 variances apart — like two bell curves that barely overlap. That's a huge effect, not a marginal one.

**Bottom line:** both an intuitive simulation and a classical formula land on the same answer — the warming is real, not sampling noise.

<!-- eof -->
