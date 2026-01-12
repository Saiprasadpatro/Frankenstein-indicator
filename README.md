# Frankenstein-indicator
TradingView Pine Script (v5) for high-probability BUY/SELL signals. Uses EMAs for trend, RSI for momentum, and volume confirmation. Green triangles = BUY, red triangles = SELL, with EMA overlays. Customizable parameters for EMAs, RSI, and volume MA. Perfect for swing and intraday traders seeking clear entries.

The **Frankenstein-indicator** is a TradingView Pine Script (v5) designed to help traders identify high-probability BUY and SELL signals by combining trend, momentum, and volume analysis.

# Features

- Detects bullish and bearish trends using fast and slow EMAs.  
- Confirms momentum with RSI within optimal ranges.  
- Validates signals using volume above its moving average.  
- Visual BUY (green triangle) and SELL (red triangle) signals on the chart.  
- Plots fast EMA (orange) and slow EMA (blue) for trend visualization.  
- Fully customizable parameters for EMAs, RSI, and volume MA.  
- Suitable for swing traders and intraday traders seeking clear entry points.

## How It Works

- **BUY Signal:** Bullish trend + RSI in 45–65 + volume above MA + bar closes higher than open.  
- **SELL Signal:** Bearish trend + RSI in 35–55 + volume above MA + bar closes lower than open.  

<img width="1919" height="907" alt="image" src="https://github.com/user-attachments/assets/b8401e2d-f2f5-4f85-8b7b-34d28ccdc427" />

## Installation

1. Copy the `Frankenstein.pine` file.  
2. Open TradingView → Pine Editor → New Script.  
3. Paste the code and save.  
4. Add the indicator to your chart.  

## Customization

Adjust the following inputs according to your trading style:

- **Fast EMA Length**  
- **Slow EMA Length**  
- **RSI Length**  
- **Volume Moving Average Length**

## License

This project is open-source. Feel free to modify and use it for personal trading purposes.

