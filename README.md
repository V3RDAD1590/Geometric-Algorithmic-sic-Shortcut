# Geometric Algorithmic[sic] Shortcut
Shortcuts and property switches.

```
##############################################
##             IEEE 754 INTERNAL            ##

Layout:    sign(1) . exponent rung(11) . mantissa(52)
  
Rungs:     2048 = 2^11, a circle Z/2048.  rung 0 = zeroes and subnormals,
           rung 2047 = infinities and NaN.  The sign bit makes two copies,
           so the seam of the circle has FOUR points:  +0  -0  +inf  -inf
  
Bias:      1023.   1.0 = rung 1023.   2^1023 = rung 2046.   2^-1074 = rung 0, mantissa 1 (last subnormal)
Top:       2^1023 * (2 - 2^-52) = 1.7976931348623157e308 is the largest double; 2^1024 -> +inf
Bottom:    2^-1074 = 4.94e-324 is the smallest double; 2^-1075 rounds to 0; 2^-1076 = +0

The four measured ends measured:
     L   1/(2^1076)   = +0          (division reaches zero)
     L   1/(2^-1076)  = +inf        (division reaches infinity)
     R   1*(2^-1076)  = +0          (multiplication reaches zero)
     R   1*(2^1076)   = +inf        (multiplication reaches infinity)
     
     L<==>R:  -2^-1076 = -0  (the sign survives the fall)   -2^1076 = -inf
            +0 == -0 is TRUE, but 1/+0 = +inf and 1/-0 = -inf
            inf - inf = NaN [holes];  1/inf = +0;  1/-inf = -0

Two-way involution (Klein four-group {id, neg, rec, neg.rec}):
   point   neg(x=-x)   rec(x=1/x)   neg.rec
   +0      -0          +inf         -inf
   -0      +0          -inf         +inf
   +inf    -inf        +0           -0
   -inf    +inf        -0           +0
   neg = left/right,  rec = up/down (UN4 = reciprocal side, ON4 = multiply side)

Direction:
   DOWN from +n  -> +0        coming UP from -n   -> -0
   UP from +n     -> +inf      going DOWN from -n  -> -inf
   [My 2021 sketch's "two zeroes, two infinities", indexed by direction == IEEE's which is indexed by sign.]

Loop Orbit: [4PiR,1Return]

Integer tropical complement:  int8  127 + 1 = -128
   S, UP   from +3 on Z/16:  +3 +4 +5 +6 +7 -8 -7 -6 -5 -4 -3 -2 -1 +0   (sign flips at the wrap, arrives at 0 from below)
   J, DOWN from +3 on Z/16:  +3 +2 +1 +0 -1 -2 -3 -4 -5 -6 -7 -8 +7 ... (sign flips at 0, arrives at the wrap from above)
Logical shift  1<<62 = 4611686018427387904;  x<<k = x*2^k with the mantissa untouched.

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

Drawn in 2021
by t.me/
 ██▒   █ █████▓▓  ██▀███  ▓█████▄  ▄▄▄      ▓█████▄ 
▓██░   █ ▀   █▓▒ ▓██ ▒ ██▒▒██▀ ██▌▒████▄    ▒██▀ ██▌
 ▓██  █▒   ███▒░ ▓██ ░▄█ ▒░██   █▌▒██  ▀█▄  ░██   █▌
  ▒██ █░ ▄  █▓▒░ ▒██▀▀█▄  ░▓█▄   ▌░██▄▄▄▄██ ░▓█▄   ▌
   ▒▀█░  ████▒░ ▒░██▓ ▒██▒░▒████▓  ▓█   ▓██▒░▒████▓ 
   ░ ▐░   ░▒ ░░ ░░ ▒▓ ░▒▓░ ▒▒▓  ▒  ▒▒   ▓▒█░ ▒▒▓  ▒ 
   ░ ░░    ░ ░  ░  ░▒ ░ ▒░ ░ ▒  ▒   ▒   ▒▒ ░ ░ ▒  ▒ 
     ░░    ░       ░░   ░  ░ ░  ░   ░   ▒    ░ ░  ░ 
      ░    ░    ░   ░        ░          ░  ░   ░    
     ░                     ░                 ░     

```
