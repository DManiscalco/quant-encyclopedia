# quant-encyclopedia
Information on quant topics and finance in general, created for job prep but hopefully something that can help others as well

## Fixed Income

### Bonds

#### [Pricing](https://corporatefinanceinstitute.com/resources/fixed-income/bond-pricing/) -- [Calculator Link](https://www.omnicalculator.com/finance/bond-price)

  - Take the present value of all payments (coupon and face), discounted using the Yield-to-Maturity (YTM) <br>
    - t: current period, T: number of periods to maturity, $C_{t}$: coupon of period t, YTM: Yield-to-Maturity, FaceValue: the face value of the bond <br>
    - Price = $\Sigma_{t=1}^{T}\frac{C_{t}}{(1+YTM)^{t}} + \frac{(FaceValue)}{(1+YTM)^{t}}$ (Annual Coupons) <br>
    - Price = $\Sigma_{t=1}^{T}\frac{C_{t}}{(1+\frac{YTM}{2})^{t}} + \frac{(FaceValue)}{(1+\frac{YTM}{2})^{t}}$ (Semi-Annual Coupons) <br>
  - Price $\uparrow$ means YTM $\downarrow$ and vice versa <br>

#### [Macaulay Duration](https://www.investopedia.com/terms/m/macaulayduration.asp) -- [Calculator Link](https://dqydj.com/bond-duration-calculator/)

  - Weighted average time to receive cash flows of bond <br>
    - t: current period, T: number of periods to maturity, $PV_{t}$: present value of the current coupon <br>
    - Macaulay Duration = $\frac{1}{T} * \frac{1}{Bond\ Price}\Sigma_{t=1}^{T}t * PV_{t}$ <br>

#### [Modified Duration](https://www.investopedia.com/terms/m/modifiedduration.asp) -- [Calculator Link](https://dqydj.com/bond-duration-calculator/)

  - Percent change in bond price due to a 1% change in interest rates <br>
    - n: number of coupon periods per year <br>
    - Modified Duration = $\frac{Macaulay\ Duration}{1 + \frac{YTM}{n}}$ <br>
   
#### [Convexity](https://www.investopedia.com/terms/c/convexity.asp#:~:text=Convexity%20demonstrates%20how%20the%20duration,said%20to%20have%20positive%20convexity.) -- [Calculator Link](https://www.omnicalculator.com/finance/bond-convexity)

  - Convexity is the second derivative of bond price movement with respect to yield (also the change in duration due to a change in yield) <br>
    - $P_{-}$: price below, $P_{+}$: price above, $P_{0}$: current price, $\Delta y$: change in interest rate in decimal form <br>
      - Convexity Approximation = $\frac{P_{+} + P_{-} - 2P_{0}}{2P_{0}(\Delta y)^{2}}$ <br>
    - [Further Convexity Information](https://www.wallstreetmojo.com/convexity-of-a-bond-formula-duration/) <br>
    - $P$: bond price, y: YTM in decimal form, t: current period, T: number of periods, $CF_{t}$: cash flow at time t <br>
      - Convexity (more precise) = $\frac{1}{P * (1+y)^{2}}\Sigma_{t=1}^{T}[\frac{CF_{t}}{(1+y)^{t}}(t^{2}+t)]$ <br>

#### [Price Change with Duration and Convexity](https://pages.stern.nyu.edu/~igiddy/articles/duration-convexity.htm)

  - $\Delta P$: change in price, P: price, $\Delta y$: change in YTM <br>
    - $\frac{\Delta P}{P} \approx -ModDuration*\Delta y + \frac{Convexity}{2}(\Delta y)^{2}$ -- (this comes from Taylor series) <br>
    - % Change in Price $\approx -ModDuration*\Delta y + \frac{Convexity}{2}(\Delta y)^{2}$ -- (where $\Delta y$ is in %) <br>
    - [Extra Info](https://www.wallstreetmojo.com/convexity-of-a-bond-formula-duration/) <br>

## Options

### Option Pricing

  - Expectation w.r.t. the distribution: $S_{T}$: $ln(S_{T}) \sim N(ln(S_{0}) + (r-\frac{\sigma^{2}}{2})T, \sigma^{2}T)$ <br>
  - Call Option: $c=e^{-rT}\mathbf{E}[S_{T}-K]^{+}$ <br>
  - Put Option: $p=e^{-rT}\mathbf{E}[K-S_{T}]^{+}$ <br>
  - Put-Call Parity: $c-p=S_{0}-Ke^{-rT}$ <br>
    - Derived through the following identity: $(a-b)^{+}-(b-a)^{+}=a-b$ <br>

### Black-Scholes Formula (to price Vanilla Options)

  - Without dividends: <br>
    - Call Option: $c=S_{t}\Phi(d_{1})-Ke^{-r(T-t)}\Phi(d_{2})$ <br>
    - Put Option: $p=-S_{t}\Phi(-d_{1})+Ke^{-r(T-t)}\Phi(-d_{2})$ <br>
      - where: $d_{1}=d_{2}+\sigma \sqrt{T-t}$ and $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>
    - With dividends: <br>
      - Call Option: $c=S_{t}e^{-q(T-t)}\Phi(d_{1})-Ke^{-r(T-t)}\Phi(d_{2})$ <br>
      - Put Option: $p=-S_{t}e^{-q(T-t)}\Phi(-d_{1})+Ke^{-r(T-t)}\Phi(-d_{2})$ <br>
        - where: $d_{1}=d_{2}+\sigma \sqrt{T-t}$ and $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-q-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>

### [Greeks](https://www.macroption.com/black-scholes-formula/#d1-d2) -- [Calculator Link](https://www.barchart.com/options/options-calculator)

  - $d_{1}=\frac{ln(\frac{S_{t}}{K})+(r-q+\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>
  - $d_{2}=\frac{ln(\frac{S_{t}}{K})+(r-q-\frac{\sigma^{2}}{2})(T-t)}{\sigma \sqrt{T-t}}$ <br>
  - $\phi(z) = \frac{1}{\sqrt{2\pi}}e^{\frac{-z^{2}}{2}}$ (PDF of the standard normal)<br>
  - $\Phi(z) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{z} e^{-\frac{{u^{2}}}{2}}du$ (CDF of the standard normal)<br>

#### [Delta](https://www.merrilledge.com/investment-products/options/learn-understand-delta-options) ($\Delta$)

  - Call: $\Delta_{c} = \frac{\partial c}{\partial S_{t}} = e^{-q(T-t)}\Phi(d_{1})$ <br>
  - Put: $\Delta_{p} = \frac{\partial p}{\partial S_{t}} = e^{-q(T-t)}(\Phi(d_{1})-1) = -e^{-q(T-t)}\Phi(-d_{1})$ <br>

#### [Gamma](https://www.merrilledge.com/investment-products/options/learn-understand-gamma-options) ($\Gamma$)

  - Call/Put: $\Gamma = \frac{\partial^{2}c}{\partial S_{t}^{2}} = \frac{\partial^{2}p}{\partial S_{t}^{2}} = \frac{e^{-q(T-t)}\phi(d_{1})}{S_{t}\sigma\sqrt{T-t}}$ <br>

#### [Theta](https://www.merrilledge.com/investment-products/options/learn-understand-theta-options) ($\Theta$)

  - Call: $\Theta_{c} = \frac{\partial c}{\partial t} = -\frac{\sigma e^{-q(T-t)} S_{t}\phi(d_{1})}{2\sqrt{T-t}} - rKe^{-r(T-t)}\Phi(d_{2}) + qS_{t}e^{-q(T-t)}\Phi(d_{1})$ <br>
  - Put: $\Theta_{p} = \frac{\partial p}{\partial t} = -\frac{\sigma e^{-q(T-t)} S_{t}\phi(d_{1})}{2\sqrt{T-t}} + rKe^{-r(T-t)}\Phi(-d_{2}) - qS_{t}e^{-q(T-t)}\Phi(-d_{1})$ <br>

#### [Vega](https://www.merrilledge.com/investment-products/options/learn-understand-vega-options) ($\nu$)

  - Call/Put: $\nu = \frac{\partial c}{\partial \sigma} = \frac{\partial p}{\partial \sigma} = e^{-q(T-t)}S_{t}\phi(d_{1})\sqrt{T-t}$ <br>

#### [Rho](https://www.merrilledge.com/investment-products/options/learn-understand-rho-options) ($\rho$)

  - Call: $\rho_{c} = \frac{\partial c}{\partial r} = K(T-t)e^{-r(T-t)}\Phi(d_{2})$ <br>
  - Put: $\rho_{p} = \frac{\partial p}{\partial r} = -K(T-t)e^{-r(T-t)}\Phi(-d_{2})$ <br>

### Black-Scholes Equation

  - $\frac{\partial V}{\partial t}+\frac{1}{2}\sigma^{2}S^{2}\frac{\partial^{2}V}{\partial S^{2}}+rS\frac{\partial V}{\partial S}-rV=0$

