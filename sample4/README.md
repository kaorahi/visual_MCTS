# MCTS visualization sample 4

(from ["Can you catch smily?"](https://www.youtube.com/watch?v=UjlxGCdjcCk))

Just a very quick experiment related to the idea ["this stone should run away"](https://github.com/lightvector/KataGo/issues/1031#issuecomment-2746727449). Interesting that combining the humanSL 9k policy was necessary to solve it.

* Naive handmade MCTS using KataGo's 18b NN. The MCTS "value" is replaced from winrate to ownership at Tengen. (To be exact, the mixture of them in a 1 : 1e+8 ratio.)
* The standard 18b policy is so sharp that white never even attempted to escape after black's wrong move. (Diagram A: truncated to [200 nodes](https://kaorahi.github.io/visual_MCTS/sample4/18b_200nodes.html), [1600 nodes](https://kaorahi.github.io/visual_MCTS/sample4/18b_1600nodes.html))
  * Hover over a node to see details. Click a node to view the PV. Press `i`, `o`, or `p` to adjust the zoom.
  * Even from the position after several moves, white never considered escaping. (Diagram B: truncated to [200 nodes](https://kaorahi.github.io/visual_MCTS/sample4/18b_cont1_200nodes.html), [1600 nodes](https://kaorahi.github.io/visual_MCTS/sample4/18b_cont1_1600nodes.html))
  * When the next move was manually forced, it suddenly noticed a chance to escape (red nodes). ([Diagram C](https://kaorahi.github.io/visual_MCTS/sample4/18b_cont2.html))
  * Just to note, adjusting the PUCT coefficient or the temperature scaling didn't seem to help, at least in very quick tests.
* By averaging the standard 18b policy and the humanSL 9k policy, it successfully found the expected solution. The key part of the problem is at least solved, though the solution doesn't go to the end and includes many unrelated nodes. Click the root node to check the PV. (Diagram D: truncated to [200 nodes](https://kaorahi.github.io/visual_MCTS/sample4/human9k_200nodes.html), [1600 nodes](https://kaorahi.github.io/visual_MCTS/sample4/human9k_1600nodes.html))

[Source code](https://github.com/kaorahi/lizgoban/tree/runaway_250325a): Shift + double-click a stone to start MCTS using "this stone should run away" behavior. Make sure to specify `-human-model` in the KataGo settings.

[Home](https://kaorahi.github.io/visual_MCTS/)
