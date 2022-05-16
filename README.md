# ML_Class10
## LLL: Catastrophic Forgetting
1. 把過去的資料想成是舊有的任務，而把來自使用者的feedback的資料當成是新的任務 -> Life-long learning
2. LLL的難點出在哪裡？Catastrophic forgetting
3. Forward Transfer: 在尚未看過某個任務，只看過其他任務時，機器到底學習到什麼程度了？
   Backward Transfer: 主要去看機器的遺忘程度，剛學完任務1，跟學完各種任務後，準確度會差多少！
## LLL: Mitigating Catastrophic Forgetting
### 3個LLL的可能解法
1. Selective Synaptic Plasticity
新的任務只去修改對過去任務不重要的參數就好！
2. How to find bi?
3. 改變訓練任務的順序，訓練結果會差很多！

## Compression: Pruning and the Lottery Ticket Hypothesis
我們是否能把碩大的模型，將它縮小，將它簡化，使他有較少的參數，但和原本的效能是差不多的呢？
### Network Pruning
1. 修剪的單位可以以參數為單位，也可以神經元為單位，兩者有何不同呢？

  for 參數：可能導致修剪後的network變成不規則的，導致實作會變得很困難、GPU也難以加速之（因不容易以矩陣的方式來做加速）-> 把修剪掉的參數設為0，但代表network沒有真的變小，因為你還是存了一個參數0！
  
  for 神經元：Network的架構仍然是有規則的！
2. 如果先train一個小的network，再把它慢慢變大，這樣會比較好嗎？ -> 不會！

   因為大的network比較好訓練！由小變大的netwrok的正確率無法跟由大變小的network的正確率相比！
   
## Compression: Knowledge Distillation
### Knowledge Distillation
根據大的network(teacher network)來製造小的network(student network)
1. Ensemble是什麼？
   
   把多個模型的輸出，平均下來當作是最終的答案！
   
2. 如果teacher network跟student network差太多的話，可否在中間加另一個network去協助student network的training？ 可以！

### Parameter Quantization:能不能使用比較少的空間來儲存parameter？
### Architecture Design: 透過netwrok架構的設計來達到減少參數量的效果！
### Dynamic Computation: 希望network可以自由的調整其運算量！（將同一個network跑在各種device上，但每個device可用的運算資源不一樣多！）
1. 讓network可以自由的調整期深度
2. 讓network可以自由決定其寬度
 
