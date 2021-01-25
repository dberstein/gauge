# GAUGE #

Usage:

    $ gauge [<type=float>] <value=0> [<scale=100>]
    $ gauge-<type> <value=0> [<scale=100>]


## Type: `float` (% of `<scale>`) ##
Maps **value** to a float percentage value in range `0..<scale>`, where `<scale>` is 100%.

    $ gauge 1000 4000
    $ 25.00%
    $ gauge float 1000 4000
    $ 25.00%
    $ gauge-float 1000 4000
    $ 25.00%

## Type: `domino` (% in range `-10..0..10`) ##
Maps **value** to a value in range `0..10` with domino glyph:
  | `+n`        | `glyph`                          | `-n`           |
  | ---         | ---                              | ---            |
  | `0   .. 9`    | **[ 0 : 0 ]**                  | `-0   .. -9`   | 
  | `10  .. 19`   | **[ 1 : 0 ]** \| **[ 0 : 1 ]** | `-10  .. -19`  |
  | `20  .. 29`   | **[ 2 : 0 ]** \| **[ 0 : 2 ]** | `-20  .. -29`  |
  | `30  .. 39`   | **[ 3 : 0 ]** \| **[ 0 : 3 ]** | `-30  .. -39`  |
  | `40  .. 49`   | **[ 4 : 0 ]** \| **[ 0 : 4 ]** | `-40  .. -49`  |
  | `50  .. 59`   | **[ 5 : 0 ]** \| **[ 0 : 5 ]** | `-50  .. -59`  |
  | `60  .. 69`   | **[ 6 : 0 ]** \| **[ 0 : 6 ]** | `-60  .. -69`  |
  | `70  .. 79`   | **[ 6 : 1 ]** \| **[ 1 : 6 ]** | `-70  .. -79`  |
  | `80  .. 89`   | **[ 6 : 2 ]** \| **[ 2 : 6 ]** | `-80  .. -89`  |
  | `90  .. 99`   | **[ 6 : 3 ]** \| **[ 3 : 6 ]** | `-90  .. -99`  |
  | `100 .. 109`  | **[ 6 : 4 ]** \| **[ 4 : 6 ]** | `-100 .. -109` |

    $ gauge domino 50
    $ 🁔
    $ gauge-domino -50
    $ 🀶

Each domino glyph represents a 10% range:

    $ seq 109 -5 -109 | xargs -I{} sh -c 'echo -n "gauge-domino {}: "; ./gauge-domino {}' | column -t
    gauge-domino  109:   🁓
    gauge-domino  104:   🁓
    gauge-domino  99:    🁌
    gauge-domino  94:    🁌
    gauge-domino  89:    🁅
    gauge-domino  84:    🁅
    gauge-domino  79:    🀾
    gauge-domino  74:    🀾
    gauge-domino  69:    🀷
    gauge-domino  64:    🀷
    gauge-domino  59:    🀶
    gauge-domino  54:    🀶
    gauge-domino  49:    🀵
    gauge-domino  44:    🀵
    gauge-domino  39:    🀴
    gauge-domino  34:    🀴
    gauge-domino  29:    🀳
    gauge-domino  24:    🀳
    gauge-domino  19:    🀲
    gauge-domino  14:    🀲
    gauge-domino  9:     🀱
    gauge-domino  4:     🀱
    gauge-domino  -1:    🀱
    gauge-domino  -6:    🀱
    gauge-domino  -11:   🀸
    gauge-domino  -16:   🀸
    gauge-domino  -21:   🀿
    gauge-domino  -26:   🀿
    gauge-domino  -31:   🁆
    gauge-domino  -36:   🁆
    gauge-domino  -41:   🁍
    gauge-domino  -46:   🁍
    gauge-domino  -51:   🁔
    gauge-domino  -56:   🁔
    gauge-domino  -61:   🁛
    gauge-domino  -66:   🁛
    gauge-domino  -71:   🁜
    gauge-domino  -76:   🁜
    gauge-domino  -81:   🁝
    gauge-domino  -86:   🁝
    gauge-domino  -91:   🁞
    gauge-domino  -96:   🁞
    gauge-domino  -101:  🁟
    gauge-domino  -106:  🁟
