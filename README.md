# 聆聽前輩們的論文發表以及活動演講工作坊的筆記紀錄  
（簡報PPT中有撰寫筆記）
## From-Quantum-Computing-to-Large-Models-Recent-Advances-and-Results-notes 劉宸銉博士  
主要在探討量子運算與大型深度學習模型（像 GPT、Transformer）之間的結合與最新進展。雖然量子硬體還不成熟，但結合大型模型的研究正在展開，目標是未來能在參數規模與訓練效率上展現量子優勢。  

## Large Scale Quantum Circuit Simulation on HPC platform  (李泰岳博士)國家實驗研究院  
主要在說台灣國網中心怎麼用超級電腦來幫忙跑量子電路模擬。因為現在真正的量子電腦還有很多限制（量子位數不夠多、雜訊太大），所以就用 HPC（高效能運算）來模擬大規模量子計算。量子電腦與 HPC 結合：利用張量網路 (Tensor Network) 方法，在 CPU/GPU 上高效模擬量子電路，解決當前量子硬體 qubit 數少、雜訊大的限制。也提到怎麼模擬量子電路：用 GPU + 張量網路的方法，把原本量子硬體做不到的實驗，在 HPC 上跑出來。

## 量子產業講座 Tiny Quantum Giant Revolution 
訪談紀錄  https://hackmd.io/@Dsv0suEvTomkyZUCTYt0eQ/S1BnL-3Yle   

## Road to Quantum Utility Workshop 探討 100+ Qubits 實用化挑戰與應用  (臺大-IBM量子中心)   
---**NTU_Workshop_Qiskit_1.0_Overview**   
介紹 Qiskit 最新的功能和發展方向。Qiskit 已經不只是寫量子電路的工具，而是變成一個能在不同硬體上用、又快又穩的「量子運算平台」。裡面提到它的效能進步很大（像是可以跑到 5000 個量子閘）、還加上 AI 幫忙最佳化電路；也有跨平台的測試數據，證明 Qiskit 比其他同類工具更省資源更有效率。除此之外，它推出一些加速研究的外掛工具和函數目錄，方便做化學、最佳化、機器學習等應用。最後還有開發輔助（Code Assistant）、學習課程，以及新版 1.0 把一些舊功能整理刪除，讓整個更乾淨、好用。  
  
---**NTU_Workshop_Quantum_Machine_Learning**  
主要在介紹量子機器學習 (QML) 的核心觀念和實作方法。內容先從機器學習的基本原理出發，說明監督式、非監督式與強化學習的差異，再引入量子版本：用參數化量子電路（variational circuits）來做分類，並解釋不同的資料編碼方式（像是 basis、amplitude、angle 等）。接著介紹量子核方法（quantum kernels）如何搭配支援向量機（SVM）展現量子優勢，最後延伸到量子神經網路（QNNs）、量子卷積網路（QCNNs）等模型，並討論訓練過程可能遇到的 barren plateau 問題。  
  
---**NTU_Workshop_Chemistry_submit**   
介紹量子化學與 Hamiltonian 模擬的應用。他先說為什麼需要量子電腦來處理化學與材料科學問題，例如藥物設計、能源優化等，因為這些模擬在傳統電腦上幾乎無法有效計算。接著介紹薛丁格方程與 Hamiltonian（系統總能量算符），並說明如何用不同模型（如 Ising、Hubbard）描述電子與自旋系統。主題也涵蓋 Pauli 矩陣與 Jordan–Wigner 映射（公式有點複雜），展示如何把分子哈密頓量轉換成量子電腦可執行的電路。最後透過氫分子模擬範例，展示隨著 qubit 數量增加，模擬結果會更接近精確解，說明量子電腦在模擬分子結構與化學反應上的潛力。  
  
---**execution-on-noisy-quantum-hardware**  
介紹如何在目前仍充滿雜訊的量子電腦上執行演算法。內容先說明量子電腦常見的雜訊來源（像是退相干、閘門誤差、讀出誤差、量子比特間干擾），然後介紹了兩大類方法來「對抗噪聲」：誤差抑制 (Error suppression)：在電路編譯或執行過程中調整，讓雜訊影響最小，例如 動態解耦 (Dynamical Decoupling, DD) 與 Pauli Twirling (PT)；誤差緩解 (Error mitigation)：在運算後透過數學方法還原比較接近真實的結果，例如 Twirled Readout Error eXtinction (TREX) 與 Zero Noise Extrapolation (ZNE)。也強調 IBM 的 Qiskit Runtime Primitives（Sampler、Estimator）已內建這些選項，使用者可以選擇合適的誤差處理策略，甚至組合多種技術來提升結果的可信度。最後也提到，這些方法是「容錯量子電腦」出現之前的重要過渡技術，幫助我們在噪聲環境下依舊能做出有意義的科學實驗。  
  
---**qiskit-addons**  
介紹 Qiskit SDK 之外的進階研究工具，用來幫助設計更大規模、效能更好的量子演算法。強調 Qiskit Addons 是模組化的「外掛」，能直接插入工作流程，搭配 Qiskit SDK 使用。重點包括四個代表性工具：  
Multi-product formulas (MPF)：透過多種 Trotter 分解組合來降低模擬中的演算法誤差。  
AQC-Tensor：利用張量網路壓縮電路前段，讓更多深度可以用於後續時間演化。  
Operator backpropagation (OBP)：以減少電路深度為代價，增加算符測量數量，換取更抗雜訊的結果。  
Sample-based Quantum Diagonalization (SQD)：結合經典分散式運算，從雜訊樣本中提取更準確的能量特徵值。  
整體來說，這些 Addons 是 IBM 把最新研究成果封裝成可直接下載使用的工具，目標是協助研究者在「utility scale」的硬體限制下，仍能進行更有效的量子化學模擬、時間演化與能量估算。    

## Introduction of Quantum Walk_CUDA0  (張晏瑞博士)   
介紹量子漫步 (Quantum Walk, QW) 的基本概念與應用。它從經典隨機漫步（Classical Random Walk）出發，說明量子版本如何利用疊加與干涉來模擬系統動態。內容重點放在離散時間量子漫步 (Discrete-Time Quantum Walk, DTQW)，算是對量子漫步的入門導讀。包括：  
Hilbert 空間結構：由「coin space（擲幣空間）」與「position space（位置空間）」組成。    
運算子設計：藉由不同的 coin operator（如 Pauli-X、Z、Hadamard）結合 shift operator 來控制漫步的演化。    
實驗與展示：展示初始狀態與不同幣算符下的演化結果，顯示量子漫步能展現比經典隨機漫步更複雜的分布特性。  






