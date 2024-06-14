# quant-encyclopedia
Information on quant topics and finance in general, created for job prep but hopefully something that can help others as well

===================================================================
# Table of Contents
<!--ts-->
   * [Black-Scholes](#black-scholes)
      * [Assumptions](#assumptions)
      * [Black-Scholes Model/Formula](#black-scholes-modelformula)
      * [Black-Scholes Equation](#black-scholes-equation)
   * [Equities](#equities)
      * [Stocks](#stocks)
        * [Stock Price Dynamics](#stock-price-dynamics----gbm)
   * [Fixed Income](#fixed-income)
      * [Bonds](#bonds)
        * [Pricing](#pricing----calculator-link)
        * [Macaulay Duration](#macaulay-duration----calculator-link)
        * [Modified Duration](#modified-duration----calculator-link)
        * [Convexity](#convexity----calculator-link)
        * [Price Change with Duration and Convexity](#price-change-with-duration-and-convexity)
   * [Interest Rate Models](#interest-rate-models)
     * [Hull-White Model](#hull-white-model)
     * [Cox-Ingersoll-Ross Model](#cox-ingersoll-ross-model)
   * [Options](#options)
     * [Option Pricing](#option-pricing)
     * [Black-Scholes Formula (to price Vanilla Options)](#black-scholes-formula-to-price-vanilla-options)
     * [Greeks](#greeks----calculator-link)
       * [Delta](#delta-delta)
       * [Gamma](#gamma-gamma)
       * [Theta](#theta-theta)
       * [Vega](#vega-nu)
       * [Rho](#rho-rho)
       * [Delta Gamma Vega Approximation](#delta-gamma-vega-approximation-by-taylor-series)
     * [Greeks Movements](#greeks-movements)
   * [Statistics](#statistics)
     * [Linear Regression](#linear-regression)
       * [Linear Regression Assumptions](#linear-regression-assumptions)
       * [Simple Linear Model](#simple-linear-model)
       * [Parameter Estimation](#parameter-estimation)
       * [Parameter Estimation Properties](#parameter-estimation-properties)
<!--te-->
===================================================================

# Black-Scholes

## [Assumptions](https://www.macroption.com/black-scholes-assumptions/)

  - Risky asset with:<br>
    - Random walk<br>
    - Constant volatility ($\sigma$)<br>
    - Normal distribution of returns on risky asset<br>
  - Riskless asset with:<br>
    - Constant risk-free rate ($r$)<br>
  - Market with:<br>
    - No transaction costs<br>
    - Perfect liquidity<br>
    - Ability to trade fractions of shares<br>
    - Short selling available<br>
    - No arbitrage<br>

## Black-Scholes Model/Formula

  - Call Option: $c=S_{t}\Phi(d_{1})-Ke^{-r(T-t)}\Phi(d_{2})$ <br>
  - Put Option: $p=-S_{t}\Phi(-d_{1})+Ke^{-r(T-t)}\Phi(-d_{2})$ <br>
    - where: $d_{1}=d_{2}+\sigma \sqrt{T-t}$ and $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>

## Black-Scholes Equation

  - $\frac{\partial V}{\partial t}+\frac{1}{2}\sigma^{2}S^{2}\frac{\partial^{2}V}{\partial S^{2}}+rS\frac{\partial V}{\partial S}-rV=0$ <br>

# Equities

## Stocks

### Stock Price Dynamics -- [GBM](https://www.columbia.edu/~mh2078/FoundationsFE/BlackScholes.pdf)

- $\frac{dS_{t}}{S_{t}} = (r-q)dt + \sigma dB_{t}$ <br>
- $S_{t} = S_{0}e^{(r-q-\frac{\sigma^{2}}{2})t + \sigma B_{t}}$ <br>
- $S_{T}$ follows a lognormal distribution: $ln(S_{T}) \sim N(ln(S_{0}) + (r-q-\frac{\sigma^{2}}{2})T, \sigma^{2}T)$ <br>

# Fixed Income

## Bonds

### [Pricing](https://corporatefinanceinstitute.com/resources/fixed-income/bond-pricing/) -- [Calculator Link](https://www.omnicalculator.com/finance/bond-price)

  - Take the present value of all payments (coupon and face), discounted using the Yield-to-Maturity (YTM) <br>
    - t: current period, T: number of periods to maturity, $C_{t}$: coupon of period t, YTM: Yield-to-Maturity, FaceValue: the face value of the bond <br>
    - Price = $\Sigma_{t=1}^{T}\frac{C_{t}}{(1+YTM)^{t}} + \frac{(FaceValue)}{(1+YTM)^{t}}$ (Annual Coupons) <br>
    - Price = $\Sigma_{t=1}^{T}\frac{C_{t}}{(1+\frac{YTM}{2})^{t}} + \frac{(FaceValue)}{(1+\frac{YTM}{2})^{t}}$ (Semi-Annual Coupons) <br>
  - Price $\uparrow$ means YTM $\downarrow$ and vice versa <br>

### [Macaulay Duration](https://www.investopedia.com/terms/m/macaulayduration.asp) -- [Calculator Link](https://dqydj.com/bond-duration-calculator/)

  - Weighted average time to receive cash flows of bond <br>
    - t: current period, T: number of periods to maturity, $PV_{t}$: present value of the current coupon <br>
    - Macaulay Duration = $\frac{1}{Bond\ Price}\Sigma_{t=1}^{T}t * PV_{t}$ <br>

### [Modified Duration](https://www.investopedia.com/terms/m/modifiedduration.asp) -- [Calculator Link](https://dqydj.com/bond-duration-calculator/)

  - Percent change in bond price due to a 1% change in interest rates <br>
    - n: number of coupon periods per year <br>
    - Modified Duration = $\frac{Macaulay\ Duration}{1 + \frac{YTM}{n}}$ <br>
   
### [Convexity](https://www.investopedia.com/terms/c/convexity.asp#:~:text=Convexity%20demonstrates%20how%20the%20duration,said%20to%20have%20positive%20convexity.) -- [Calculator Link](https://www.omnicalculator.com/finance/bond-convexity)

  - Convexity is the second derivative of bond price movement with respect to yield (also the change in duration due to a change in yield) <br>
    - $P_{-}$: price below, $P_{+}$: price above, $P_{0}$: current price, $\Delta y$: change in interest rate in decimal form <br>
      - Convexity Approximation = $\frac{P_{+} + P_{-} - 2P_{0}}{2P_{0}(\Delta y)^{2}}$ <br>
    - [Further Convexity Information](https://www.wallstreetmojo.com/convexity-of-a-bond-formula-duration/) <br>
    - $P$: bond price, y: YTM in decimal form, t: current period, T: number of periods, $CF_{t}$: cash flow at time t <br>
      - Convexity (more precise) = $\frac{1}{P * (1+y)^{2}}\Sigma_{t=1}^{T}[\frac{CF_{t}}{(1+y)^{t}}(t^{2}+t)]$ <br>

### [Price Change with Duration and Convexity](https://pages.stern.nyu.edu/~igiddy/articles/duration-convexity.htm)

  - $\Delta P$: change in price, P: price, $\Delta y$: change in YTM <br>
    - $\frac{\Delta P}{P} \approx -ModDuration*\Delta y + \frac{Convexity}{2}(\Delta y)^{2}$ -- (this comes from Taylor series) <br>
    - % Change in Price $\approx -ModDuration*\Delta y + \frac{Convexity}{2}(\Delta y)^{2}$ -- (where $\Delta y$ is in %) <br>
    - [Extra Info](https://www.wallstreetmojo.com/convexity-of-a-bond-formula-duration/) <br>

# Interest Rate Models

## Hull-White Model

  - $dR_{t}=(a_{t}-b_{t}R_{t})dt+\sigma_{t}dW_{t}$ where $a_{t}$, $b_{t}$, and $\sigma_{t}$ are deterministic and positively valued, and $W_{t}$ is a driftless Brownian Motion under $Q$<br>
  - NOTE: In this model, it is possible for $R_{t}$ to go negative

## Cox-Ingersoll-Ross Model

  - $dR_{t}=(a-bR_{t})dt+\sigma\sqrt{R_{t}}dW_{t}$ where $a$, $b$, and $\sigma$ are deterministic and positively valued, and $W_{t}$ is a driftless Brownian Motion under $Q$<br>
  - NOTE: $\sqrt{R_{t}}$ means that $R_{t}$ will not go negative

# Options

## Option Pricing

  - Expectation w.r.t. the distribution: $S_{T}$: $ln(S_{T}) \sim N(ln(S_{0}) + (r-\frac{\sigma^{2}}{2})T, \sigma^{2}T)$ <br>
  - Call Option: $c=e^{-rT}\mathbf{E}[S_{T}-K]^{+}$ <br>
  - Put Option: $p=e^{-rT}\mathbf{E}[K-S_{T}]^{+}$ <br>
  - Put-Call Parity: $c-p=S_{0}-Ke^{-rT}$ <br>
    - Derived through the following identity: $(a-b)^{+}-(b-a)^{+}=a-b$ <br>

## Black-Scholes Formula (to price Vanilla Options)

  - Without dividends: <br>
    - Call Option: $c=S_{t}\Phi(d_{1})-Ke^{-r(T-t)}\Phi(d_{2})$ <br>
    - Put Option: $p=-S_{t}\Phi(-d_{1})+Ke^{-r(T-t)}\Phi(-d_{2})$ <br>
      - where: $d_{1}=d_{2}+\sigma \sqrt{T-t}$ and $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>
  - With dividends: <br>
    - Call Option: $c=S_{t}e^{-q(T-t)}\Phi(d_{1})-Ke^{-r(T-t)}\Phi(d_{2})$ <br>
    - Put Option: $p=-S_{t}e^{-q(T-t)}\Phi(-d_{1})+Ke^{-r(T-t)}\Phi(-d_{2})$ <br>
      - where: $d_{1}=d_{2}+\sigma \sqrt{T-t}$ and $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-q-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>

## [Greeks](https://www.macroption.com/black-scholes-formula/#d1-d2) -- [Calculator Link](https://www.barchart.com/options/options-calculator)

  - $d_{1}=\frac{ln(\frac{S_{t}}{K})+(r-q+\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>
  - $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-q-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>
  - $\phi(z) = \frac{1}{\sqrt{2\pi}}e^{\frac{-z^{2}}{2}}$ (PDF of the standard normal)<br>
  - $\Phi(z) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{z} e^{-\frac{{u^{2}}}{2}}du$ (CDF of the standard normal)<br>

### [Delta](https://www.merrilledge.com/investment-products/options/learn-understand-delta-options) ($\Delta$)

  - Call: $\Delta_{c} = \frac{\partial c}{\partial S_{t}} = e^{-q(T-t)}\Phi(d_{1})$ <br>
  - Put: $\Delta_{p} = \frac{\partial p}{\partial S_{t}} = e^{-q(T-t)}(\Phi(d_{1})-1) = -e^{-q(T-t)}\Phi(-d_{1})$ <br>

### [Gamma](https://www.merrilledge.com/investment-products/options/learn-understand-gamma-options) ($\Gamma$)

  - Call/Put: $\Gamma = \frac{\partial^{2}c}{\partial S_{t}^{2}} = \frac{\partial^{2}p}{\partial S_{t}^{2}} = \frac{e^{-q(T-t)}\phi(d_{1})}{S_{t}\sigma\sqrt{T-t}}$ <br>

### [Theta](https://www.merrilledge.com/investment-products/options/learn-understand-theta-options) ($\Theta$)

  - Call: $\Theta_{c} = \frac{\partial c}{\partial t} = -\frac{\sigma e^{-q(T-t)} S_{t}\phi(d_{1})}{2\sqrt{T-t}} - rKe^{-r(T-t)}\Phi(d_{2}) + qS_{t}e^{-q(T-t)}\Phi(d_{1})$ <br>
  - Put: $\Theta_{p} = \frac{\partial p}{\partial t} = -\frac{\sigma e^{-q(T-t)} S_{t}\phi(d_{1})}{2\sqrt{T-t}} + rKe^{-r(T-t)}\Phi(-d_{2}) - qS_{t}e^{-q(T-t)}\Phi(-d_{1})$ <br>

### [Vega](https://www.merrilledge.com/investment-products/options/learn-understand-vega-options) ($\nu$)

  - Call/Put: $\nu = \frac{\partial c}{\partial \sigma} = \frac{\partial p}{\partial \sigma} = e^{-q(T-t)}S_{t}\phi(d_{1})\sqrt{T-t}$ <br>

### [Rho](https://www.merrilledge.com/investment-products/options/learn-understand-rho-options) ($\rho$)

  - Call: $\rho_{c} = \frac{\partial c}{\partial r} = K(T-t)e^{-r(T-t)}\Phi(d_{2})$ <br>
  - Put: $\rho_{p} = \frac{\partial p}{\partial r} = -K(T-t)e^{-r(T-t)}\Phi(-d_{2})$ <br>

### [Delta-Gamma-Vega Approximation](https://www.columbia.edu/~mh2078/FoundationsFE/BlackScholes.pdf) (by Taylor Series)

  - Call: $c(S+\Delta S, \sigma + \Delta \sigma) \approx c(S,\sigma) + \Delta S \frac{\partial c}{\partial S} + \frac{1}{2}(\Delta S)^{2}\frac{\partial^{2} c}{\partial S^{2}} + \Delta \sigma \frac{\partial c}{\partial \sigma}$ <br>
  - Put: $p(S+\Delta S, \sigma + \Delta \sigma) \approx p(S,\sigma) + \Delta S \frac{\partial p}{\partial S} + \frac{1}{2}(\Delta S)^{2}\frac{\partial^{2} p}{\partial S^{2}} + \Delta \sigma \frac{\partial p}{\partial \sigma}$ <br>

## Greeks Movements

# Statistics

## Linear Regression

### [Linear Regression Assumptions](https://www.statisticssolutions.com/free-resources/directory-of-statistical-analyses/assumptions-of-linear-regression/)

  - Linear relationship between the dependent and independent variables<br>
  - The residuals (difference between observed values and predicted values) are normally distributed - could be done using [Q-Q plot](https://statisticsbyjim.com/graphs/qq-plot/) or a [Kolmogorov-Smirnov Test](https://www.itl.nist.gov/div898/handbook/eda/section3/eda35g.htm) among other tests<br>
  - No multicollinearity: the independent variables are not too highly correlated with each other<br>
  - [Homoscedasticity](https://www.statisticssolutions.com/free-resources/directory-of-statistical-analyses/homoscedasticity/): The variance of the residuals does not change across all values of the independent variables<br>

### Simple Linear Model

  - $Y=\beta_{0}+\beta_{1}X+\epsilon$ where: <br>
    - $\beta_{0}$ is fixed intercept parameter<br>
    - $\beta_{1}$ is fixed slope parameter<br>
    - $\epsilon$ is random error where $\mathbf{E}[\epsilon |X]=0$, $V(\epsilon |X)=\sigma^{2}$<br>
    - Under these assumptions: $\mathbf{E}[Y|X=x]=\beta_{0}+\beta_{1}x$<br>

### [Parameter Estimation](https://www.immagic.com/eLibrary/ARCHIVES/GENERAL/WIKIPEDI/W120529O.pdf)

  - Predicted value of $\hat{Y_{i}}$: $\hat{Y_{i}}=\hat{\beta_{0}}+\hat{\beta_{1}}X_{i}$ where:<br>
    - $\hat{\beta_{0}}$ and $\hat{\beta_{1}}$ are estimates of $\beta_{0}$ and $\beta_{1}$<br>
  - Residuals: $\hat{\epsilon_{i}}=Y_{i}-\hat{Y_{i}}=Y_{i}-(\hat{\beta_{0}}+\hat{\beta_{1}}X_{i})$<br>
  - Residual Sum of Squares (RSS): RSS = $\Sigma_{i=1}^{n} \hat{\epsilon}_{i}^{2}$<br>
    - Minimizing RSS gives:<br>
      - $\hat{\beta_{1}}=\frac{\Sigma_{i=1}^{n}(X_{i}-\bar{X_{n}})(Y_{i}-\bar{Y_{n}})}{\Sigma_{i=1}^{n}(X_{i}-\bar{X_{n}})^{2}}$<br>
      - $\hat{\beta_{0}}=\bar{Y_{n}}-\hat{\beta_{1}}\bar{X}_{n}$<br>
  - $\hat{\sigma}^{2}=(\frac{1}{n-2})\Sigma_{i=1}^{n}\hat{\epsilon}_{i}^{2}$<br>

### Parameter Estimation Properties

  - $V(\hat{\beta_{1}}|x_{1},...,x_{n})=\frac{\sigma^{2}}{\Sigma(x_{i}-\bar{x}_{n})^{2}}$<br>
  - $V(\hat{\beta_{0}}|x_{1},...,x_{n})=\frac{\sigma^{2}}{\Sigma(x_{i}-\bar{x}_{n})^{2}}\frac{\Sigma x_i^2}{n}$<br>
  - $Cov(\hat{\beta_{0}},\hat{\beta_{1}})=\frac{-\sigma^{2} \bar{x_{n}}}{\Sigma(x_{i}-\bar{x}_{n})^{2}}$<br>
    - When $\sigma^{2}$ is unknown, use $\hat{\sigma}^{2}$ and take the square root to get $\hat{se}(\hat{\beta_{0}})$ and $\hat{se}(\hat{\beta}_{1})$ as estimators<br>
  - [By Central Limit Theorem](https://sphweb.bumc.bu.edu/otlt/mph-modules/bs/bs704_probability/BS704_Probability12.html):
    - $\frac{\hat{\beta_{0}}-\beta_{0}}{\hat{se}(\hat{\beta_{0}})} \xrightarrow{d} N(0,1)$<br>
    - $\frac{\hat{\beta_{1}}-\beta_{1}}{\hat{se}(\hat{\beta_{1}})} \xrightarrow{d} N(0,1)$<br>
    - [Confidence Intervals](http://www.stat.yale.edu/Courses/1997-98/101/confint.htm): $\hat{\beta_{0}}\pm z_{\frac{\alpha}{2}}\hat{se}(\hat{\beta_{0}})$ and $\hat{\beta_{1}}\pm z_{\frac{\alpha}{2}}\hat{se}(\hat{\beta_{1}})$<br>
  
