# 📈 VIX Trading Strategy with Machine Learning Enhancement

> **Can we beat the market by timing volatility? A data-driven journey from simple rules to machine learning.**

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Portfolio](https://img.shields.io/badge/Project-Portfolio-purple.svg)](#)

## 🎯 The Big Idea

**What if we could predict market movements by watching fear itself?**

The VIX (Volatility Index) is often called the "Fear Gauge" - when it spikes, markets panic. When it's low, investors get complacent. This project explores whether we can systematically profit from these emotional swings using data science and machine learning.

---

## 🚀 Key Findings
**❗ Disclaimer**: There are some adjusments needed for **Simple VIX Rule** and **Enhanced Rules**.

| Strategy | Annual Return | Risk (Volatility) | Sharpe Ratio | Max Drawdown | Win Rate |
|----------|---------------|-------------------|--------------|--------------|----------|
| **🛒 Buy & Hold** | 6.7% | 19.8% | 0.34 | -56.8% | 54.0% |
| **⚡ Simple VIX Rule** | 22.8% | 19.8% | 1.16 | -29.4% | 55.1% |
| **🧠 Enhanced Rules** | 61.6% | 19.6% | 3.15 | -16.1% | 58.1% |
| **🤖 ML Strategy** | **6.8%** | **4.4%** | **1.55** | **-14.4%** | **3.8%** |

**🎉 Winner**: The ML strategy achieves superior risk-adjusted returns with dramatically lower volatility! *(and the most sensible numbers at this stage)*


---

## 📖 The Story

### 💡 The Original Hypothesis
*"When VIX is high, markets are scared → Go short and profit from the decline!"* \
Another Hypothesis: the threshold for a high VIX is 30

Simple, intuitive, and... **completely wrong** in practice! Here's why:

### 🤔 The Problems Discovered

**Problem #1: Market Regimes Change**
- VIX = 30 in 2008 ≠ VIX = 30 in 2017
- Fixed thresholds don't adapt to different volatility environments

**Problem #2: Volatility Clustering** 
- High VIX often stays high (panic persists)
- Shorting during spikes = catching a falling knife 🔪

**Problem #3: Missing Context**
- High VIX + Bull Market = Buying opportunity
- High VIX + Bear Market = More pain ahead
- Context matters more than absolute levels!

### 🛠️ The Solution

**Step 1: Adaptive Thresholds**
```python
# Instead of: VIX > 30 (static)
# Use: VIX > 80th percentile (adaptive)
vix_high = df['VIX_Percentile_252'] > 0.8
```

**Step 2: Multi-Factor Signals**
```python
# Combine: VIX Level + Market Trend + Momentum
short_signal = (vix_high) & (market_weak) & (vix_declining)
```

**Step 3: Machine Learning**
- 16 engineered features capturing volatility patterns
- Random Forest to find complex (non-linear) relationships
- Walk-forward validation (no peeking into the future, avoiding data leakage!)

---

## 🔍 What Makes This Project Special

*for me, personally!*

### 🎓 Educational Journey
- **Hypothesis → Test → Learn → Improve**
- Shows the evolution from simple ideas to sophisticated models
- Demonstrates why "obvious" strategies often fail

### 📊 Real-World Application
- Uses actual S&P 500 and VIX data from Kaggle
- Includes transaction costs and realistic assumptions
- Walk-forward validation (no hindsight bias)

### 🛡️ Risk Management Focus
- Emphasizes risk-adjusted returns over raw performance
- Comprehensive drawdown analysis
- Position sizing and volatility targeting

### 🤖 Modern Data Science
- Feature engineering for financial time series
- Machine learning for pattern recognition
- Professional code structure and documentation

---

## 🎯 Skills Gained

### 📈 **Quantitative Finance**
- Volatility modeling and mean reversion
- Risk metrics (Sharpe ratio, VaR, drawdowns)  
- Portfolio construction and backtesting
- Market microstructure understanding

### 🔬 **Data Science**
- Feature engineering (16 custom indicators)
- Time series cross-validation
- Random Forest classification
- Model interpretation and validation

### 💻 **Technical Skills**
- **Python**: Pandas, NumPy, Scikit-learn
- **Visualization**: Matplotlib, Seaborn
- **Development**: Modular code design, Git version control
- **Documentation**: Clear explanations and professional presentation

---

## 📂 Repository Structure
This is the **current** Repository Structure. Codes are still in progress, but exploration notebook is up!

```
📦 vix-trading-strategy-ml/
├── 📋 README.md                                   # You are here!
├── 📓 notebooks/
│   └── 00-vix-trading-strategy-exploration.ipynb  # Exploration and Explanation Notebook
├── 🔧 src/
│   └── __init__.py
└── 📊 data/
    ├── SPX.csv                                     # S&P 500 Historical Dataset
    └── VIX.csv                                     # VIX Index Dataset
```

---

## 🚀 Quick Start

### 1️⃣ **Clone the Repository**
```bash
git clone https://github.com/melisathevandi/vix-trading-strategy-ml.git
cd vix-trading-strategy-ml
```

### 2️⃣ **Download Data**
- [S&P 500 Historical Data](https://www.kaggle.com/datasets/henryhan117/sp-500-historical-data)
- [VIX Daily Prices](https://www.kaggle.com/datasets/maxsmyc/vix-volatility-index-daily-price)
- Place CSV files in `data/` directory

### 3️⃣ **Run the Analysis**
```bash
# Option 1: Python script (CURRENTLY UNAVAILABLE)
python -m src.main

# Option 2: Jupyter notebooks
jupyter notebook notebooks/00-vix-trading-strategy-exploration.ipynb
```

---

## 🧠 Key Insights & Lessons

*that I learned!*

### 💎 **Golden Rules Discovered**

1. **📊 Percentiles > Fixed Thresholds**
   - VIX rank matters more than absolute level
   - Adaptive signals survive regime changes

2. **⏰ Timing Beats Direction**
   - Don't short during volatility spikes
   - Wait for fear to peak, then reverse

3. **🎯 Context is King** 
   - High VIX + Strong trend = Mean reversion opportunity
   - High VIX + Weak trend = Stay defensive

4. **🤖 ML is Smart at Risk Management**
   - Lower volatility through diversified signals
   - Better downside protection
   - More consistent performance

### 🚨 **Pitfalls Avoided**

*still being improved*

- **Lookahead Bias**: Only use information available at time T
- **Overfitting**: Out-of-sample validation catches this
- **Survivorship Bias**: Test across different market regimes
- **Transaction Costs**: Include realistic trading expenses

---

## 📈 Business Impact

### 💼 **Real-World Applications**

**Asset Management:**
- Tactical allocation overlays
- Risk management systems
- Alternative risk premia strategies

**Hedge Funds:**
- Volatility arbitrage
- Market neutral strategies  
- Crisis alpha generation

**Individual Investors:**
- Portfolio hedging
- Systematic market timing
- Behavioral bias mitigation

---

## 🔮 Future Enhancements

### 🚧 **Phase 1.5 Roadmap**

- [ ] **Logic Review**: Logic review and debugging

### 🚧 **Phase 2 Roadmap**

- [ ] **Options Integration**: Use actual VIX futures and options data
- [ ] **Regime Detection**: Hidden Markov Models for market states  
- [ ] **Dynamic Position Sizing**: Kelly Criterion optimization
- [ ] **Cross-Asset Signals**: Credit spreads, currency volatility
- [ ] **Real-Time Implementation**: Live trading system
- [ ] **Deep Learning**: LSTM networks for sequence modeling

### 💡 **Research Questions**

- Can transformer models capture volatility patterns better?
- How does this strategy perform internationally?
- What's the optimal rebalancing frequency?
- How sensitive are results to transaction costs?

---

## 🎓 Summary What I Learned Personally

**🔍 Problem-Solving**: Started with simple hypothesis *(from the internet)*, discovered flaws, iteratively improved \
**📊 Technical Skills**: End-to-end data science pipeline in finance domain  \
**🎯 Business Acumen**: Focus on risk-adjusted returns and practical implementation \
**📈 Communication**: Breaking down explanations of complex quantitative concepts \
**📚 Quantitative Finance**: Real-world application of quantitative concepts \
**💻 Data Science**: Feature engineering, ML, and model validation, backtesting

---

## 📞 Connect & Discuss

### 🤝 **Let's Chat!**

I'm passionate about quantitative finance -- data science and always excited to discuss:
- Trading strategies and backtesting methodologies
- Machine learning applications in finance
- Risk management and portfolio optimization
- Career opportunities in quantitative research -- data science

**📧 Email**: [melisa.thevandi@u.nus.edu](mailto:melisa.thevandi@u.nus.edu)  
**💼 LinkedIn**: [melisa-thevandi](https://www.linkedin.com/in/melisa-thevandi)  
**🐙 GitHub**: [More Projects](https://github.com/melisathevandi)

---

## 📜 License & Disclaimer

**MIT License** - Feel free to use this code for learning and research!

**⚠️ Important Disclaimer**: This is a personal educational project. Past performance doesn't guarantee future results. Always do your own research and consider your risk tolerance before making investment decisions.

---

## 🙏 Acknowledgments

- **Data Sources**: Kaggle community for S&P 500 and VIX datasets
- **Inspiration**: Academic literature on volatility forecasting
- **Tools**: Python ecosystem (pandas, scikit-learn, matplotlib, seaborn)

---

**⭐ If you found this project helpful, please give it a star and share with others interested in quantitative finance -- data science!**

*Built with ❤️ and lots of ☕ by **Melisa Abigail Thevandi***
