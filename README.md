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
    - [Extra Info](https://www.wallstreetmojo.com/convexity-of-a-bond-formula-duration/)
