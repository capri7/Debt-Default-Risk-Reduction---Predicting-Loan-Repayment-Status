# Debt Default Risk Reduction - Predicting Loan Repayment Status

**【練習問題】債務不履行リスクの低減**  
借入総額や返済期間、金利、借入目的などの顧客データを使って、債務不履行リスクを予測するモデルを構築しました。

---

## プロジェクト概要 (Introduction)

### **概要**
本プロジェクトは「**債務不履行リスクの低減**」を目的とし、与えられた顧客データを用いて、**債務が完済されるかどうか**を予測します。

- **評価指標**: F1スコア  
- **現在の成績**: 523人中 **61位**  

### **使用データ**
- **説明変数**:  
   - `loan_amnt`: 借入総額  
   - `term`: 返済期間  
   - `interest_rate`: 金利  
   - `purpose`: 借入目的  
   - その他、計9特徴量  
- **目的変数**:  
   - `0`: Fully Paid（完済）  
   - `1`: Charged Off（債務不履行）  

### **データ概要とEDAのインサイト**
- **データの特徴**
   - サンプル数: 242,156  
   - 欠損値: employment_length に欠損値 
   - データ分布:   
   - 目的変数の分布:
   - - 完済: 80% 
   - - 債務不履行: 20%

### **主なEDA結果とインサイト**
1. Burden Index（負担指数）と Monthly Payment（月々の支払額）の関係
傾向:
Burden Index が高いほど、債務不履行の割合 が増える傾向が見られます。
返済期間（36ヶ月 と 60ヶ月）が月々の支払額に影響し、2つのクラスターに分かれます。
2. Loan Amount（借入額）と Monthly Payment（支払額）
傾向:
完済（青） と 不履行（赤） の比較において、
月々の支払額が多い場合、不履行のリスク が高まる傾向があります。
3. Credit Score と Loan Status
傾向:
信用スコア（credit_score） が低いほど、債務不履行のリスク が高くなる傾向が見られます。
4. Interest Rate（利率）
傾向:
金利（interest_rate） が高い場合、債務不履行の可能性 が増加します。

### **使用したモデルと手法**
1. モデル構築
LightGBM

F1スコア: 0.4138822

CatBoost

トレーニング中: 結果は後述予定。

2. パラメータチューニング
Optuna を使用して、最適なパラメータを探索。

3. クロスバリデーション
Stratified K-Fold（5分割）を適用し、モデルの汎化性能を確認。
 
### **結果の可視化**
- **重要な可視化結果**:
Burden Index と Monthly Payment:
Loan Amount と Monthly Payment:

- **目的変数の分布**:

### **今後の課題と改善点**
- **モデルの精度向上**:

CatBoostの結果を確認し、LightGBMとのアンサンブルを検討。

適切な閾値設定によるF1スコアの改善。

- **特徴量エンジニアリング**:

burden_index や interest_rate などの特徴量間の相互作用を検討。

- **モデル解釈**:
Permutation Importanceを用いて、特徴量の重要度を可視化。

### **環境構築**
Python: 3.8

pip install pandas numpy matplotlib seaborn lightgbm catboost optuna scikit-learn

### **まとめ**
本プロジェクトでは、顧客の債務不履行リスクを予測するためにEDAとLightGBM、CatBoostを活用しました。
現在のF1スコアは 0.4138 であり、CatBoostの結果を踏まえ、さらなる精度改善を目指します。
