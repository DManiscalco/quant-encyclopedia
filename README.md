# quant-encyclopedia
Information on quant topics and finance in general, created for job prep but hopefully something that can help others as well

## Fixed Income

### Bonds

#### [Pricing](https://corporatefinanceinstitute.com/resources/fixed-income/bond-pricing/) -- [Calculator Link](https://www.omnicalculator.com/finance/bond-price)

  - Take the present value of all payments (coupon and face), discounted using the Yield-to-Maturity (YTM) <br>
    - t: current period, T: number of periods to maturity, $C_{t}$: coupon of period t, YTM: Yield-to-Maturity, FaceValue: the face value of the bond <br>
    - Price = $\Sigma_{t=1}^{T}\frac{C_{t}}{(1+YTM)^{t}} + \frac{(FaceValue)}{(1+YTM)^{t}}$ (Annual Coupons) <br>
    - Price = $\Sigma_{t=1}^{T}\frac{C_{t}}{(1+\frac{YTM}{2})^{t}} + \frac{(FaceValue)}{(1+\frac{YTM}{2})^{t}}$ (Semi-Annual Coupons) <br>
  - Price $\uparrow$ means YTM $\downarrow$ and vice versa

#### [Macaulay Duration](https://www.investopedia.com/terms/m/macaulayduration.asp) -- [Calculator Link](https://dqydj.com/bond-duration-calculator/)

  - Weighted average time to receive cash flows of bond <br>
    - t: current period, T: number of periods to maturity, $PV_{t}$: present value of the current coupon
    - Macaulay Duration = $\frac{1}{T} * \frac{1}{Bond\ Price}\Sigma_{t=1}^{T}t * PV_{t}$

#### [Modified Duration](https://www.investopedia.com/terms/m/modifiedduration.asp) -- [Calculator Link](https://dqydj.com/bond-duration-calculator/)

  - Percent change in bond price due to a 1% change in interest rates <br>
    - n: number of coupon periods per year <br>
    - Modified Duration = $\frac{Macaulay\ Duration}{1 + \frac{YTM}{n}}$
