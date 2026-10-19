# Dividend-income-planner
Browser-based dividend income planner: project your net dividend income, reinvestment and time to reach your monthly goal. Single HTML file, no install, no server, your data stays in your browser.
# Dividend Income Planner

A simple, private dividend income projection tool that runs entirely in your browser. Enter your holdings and a few assumptions, and see how much net income your portfolio could generate each year, and when you could reach your monthly income goal.

**Live demo:** `https://YOUR-USERNAME.github.io/dividend-income-planner/`

## Features

- **Holdings table**: name, number of shares, price, dividend yield and expected dividend growth for each line. Add or remove rows freely.
- **Assumptions**: monthly contribution, time horizon (1 to 50 years), annual price growth, tax on dividends and a monthly net income goal.
- **Dividend reinvestment (DRIP)**: toggle reinvestment of net dividends into more shares.
- **Live results**: net monthly income today and at the end of the horizon, the year your goal is reached, and final portfolio value.
- **Chart and table**: a bar chart of net annual income with your goal line, plus a year-by-year breakdown of income, portfolio value and capital invested.
- **Light and dark mode**: follows your device setting.
- **Private by design**: no server, no account, no tracking. Your inputs are saved only in your own browser (`localStorage`).

## Getting started

There is nothing to install or build. The whole project is a single HTML file.

1. Download or clone this repository.
2. Open `index.html` in any modern browser.

To host it for free, enable **GitHub Pages**: go to *Settings → Pages*, select the `main` branch and the `/ (root)` folder, then save.

## How the projection works

The calculation lives in the `sim()` function in the `<script>` block of `index.html`. For each year, and for each holding, it:

1. Computes gross income as `shares × dividend per share`.
2. Applies the tax rate to get net income.
3. If reinvestment is on, buys more shares with the net income at the current price.
4. Buys more shares with the yearly contributions (12 × the monthly contribution), split in proportion to the initial value of each holding.
5. Grows the share price by the price growth assumption, and each dividend by that holding's own growth rate.

The year-by-year results are then rendered as summary cards, an SVG chart and a table.

## Customising

- **Default holdings and assumptions**: edit the `DEF` object at the top of the script.
- **Colours**: change the CSS variables in the `:root` blocks at the top of the file (`--acc` is the main accent colour).
- **Currency and number format**: change the locale and currency in the `Intl.NumberFormat` call.

## Limitations

- Dividends are treated as paid once a year, with no intra-year timing.
- No trading fees, currency effects, inflation adjustment or tax-wrapper rules.
- Contributions are always split across your existing holdings, not into new ones.
- Yields, growth rates and prices are your assumptions. The tool does not fetch market data.

## Disclaimer

This tool is for educational and planning purposes only. It is not financial, tax or investment advice, and the projections are not guarantees of future results. Past yields and dividend growth do not predict the future.

## License
MIT License

Copyright (c) 2026 Kim Dushime

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
