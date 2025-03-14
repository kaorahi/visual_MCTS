# MCTS visualization sample 2

(from KataGo issue [#990](https://github.com/lightvector/KataGo/issues/990))

This is not KataGo but a naive built-in MCTS using KataGo's neural network (kata1-b28c512nbt-s8326). Still, I expect it to give some hints.

The node colors represent estimated winrates (blue = high, red = low for Black). Use the i/o keys to zoom. Hover over a node for more details.

* [Diagram A](https://kaorahi.github.io/visual_MCTS/sample2/katago_issue990_diagram_a.html): The initial evaluation of N8 is quite positive for White, but it quickly turns unfavorable.
* Diagram B ([truncated](https://kaorahi.github.io/visual_MCTS/sample2/katago_issue990_diagram_b.html) / [full](https://kaorahi.github.io/visual_MCTS/sample2/katago_issue990_diagram_b_full.html)): (1220 visits) It seems to find a hopeful sequence "O8, M3, M6, M1, ..." for White (PV = red edges). It took long to find this because the policies of M3 and M1 are low.
* Diagram C ([truncated](https://kaorahi.github.io/visual_MCTS/sample2/katago_issue990_diagram_c.html) / [full](https://kaorahi.github.io/visual_MCTS/sample2/katago_issue990_diagram_c_full.html)): (2000 visits) The evaluation of this sequence "O8, M3, M6, M1" is still not high for White because there are many blue-to-purple nodes under M1. To improve its evaluation, it needs to find a counterplay for each child node of M1. To propagate the results to its ancestors, it also needs even more visits.
* [Diagram D](https://kaorahi.github.io/visual_MCTS/sample2/katago_issue990_diagram_d.html): For example, after the sequence "O8, M3, M6, M1, J1, K2, H1, F1, K1" (deeper in the leftmost sequence, i.e. the hightest policy sequence), it still needs 200 more visits to reach a 50% winrate.

[Home](https://kaorahi.github.io/visual_MCTS/)
