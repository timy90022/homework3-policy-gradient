# Homework3-Policy-Gradient report


## All About That Base

Ｗe can discover that the one with baseline has lower variance.

However, average return is dominated by initial configuration.

It seems that baseline does not affect gradient.

Why?

### loss = ( Σ [ Σ [ log ( policy ) * ( reward - baseline ) ] τ from 0 to T ] n from 1 to N ) / NT

Baseline is not a function of current action but reward is.

Var [ reward - baseline ] < Var [ reward ] => Var [ loss with baseline ] < Var [ loss without baseline ]

### gradient = ∇ [ loss ] w.r.t θ

Baseline is not a function of current action, so it is not a function of θ.

After differentiated by θ, it disappears.

Therefore, it does not affect gradient.


## Problem 5

`	code
	
	b_roll = np.roll(b, len(x)-1)
    b_roll[-1] = 0.0
    y = x + discount_rate * b_roll - b
    return y
`
Actor-critic should have better performance compare to previous problems.

##Problem 6. To implement the Generalized Advantage Estimation
code

> a = util.discount(a, self.discount_rate * LAMBDA)

* the average return: irregular increase


