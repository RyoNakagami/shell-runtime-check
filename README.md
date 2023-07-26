## Result

```zsh
% grep 'model name' /proc/cpuinfo |head -n1
model name      : AMD Ryzen 9 7950X 16-Core Processor

% lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:        22.04
Codename:       jammy

% bash --version |head -n1
GNU bash, version 5.1.16(1)-release (x86_64-pc-linux-gnu)

% zsh --version
zsh 5.8.1 (x86_64-ubuntu-linux-gnu)

% ksh --version
  version         sh (AT&T Research) 93u+m/1.0.0-beta.2 2021-12-17

% zsh ./shell_speed_check.sh
| bash           | ksh            | zsh            |
|  0.03 ( 100.0) |  0.01 (  29.4) |  0.02 (  58.8) | Parameter Expansion 1: "$PARAMETER"
|  0.26 ( 100.0) |  0.03 (  11.5) |  0.03 (  12.3) | Parameter Expansion 2: $PARAMETER
|  1.03 ( 100.0) |  0.49 (  47.5) |  0.95 (  92.5) | Parameter Expansion 3: "${PARAMETER##*/}" (modifier)
|  0.62 ( 100.0) |  0.02 (   3.2) |  0.32 (  51.3) | Array Parameter Expansion 1: "${ARRAY[1]}" (one element)
|  2.23 ( 100.0) |  0.16 (   7.2) |  0.26 (  11.4) | Array Parameter Expansion 2: "${ARRAY[@]}" (all elements)
|  3.19 ( 100.0) |  2.43 (  76.1) |  2.66 (  83.4) | Arithmetic Evaluation 1: let EXPRESSION
|  1.88 ( 100.0) |  1.15 (  61.2) |  0.72 (  38.6) | Arithmetic Evaluation 2: ((EXPRESSION))
|  3.31 ( 100.0) |  1.84 (  55.6) |  1.31 (  39.7) | Arithmetic Expansion 1: $((EXPRESSION))
|  3.66 ( 100.0) |  2.15 (  58.8) |  1.45 (  39.5) | Arithmetic Expansion 2: $(($PARAMETER+EXPRESSION))
|  2.77 ( 100.0) |  1.30 (  46.9) |  1.41 (  50.8) | Test 1: [[ EXPRESSION ]]
|  4.94 ( 100.0) |  1.60 (  32.4) |  4.81 (  97.5) | Test 2: [ EXPRESSION ]
|  9.16 ( 100.0) | 10.80 ( 117.9) |  4.19 (  45.7) | Fork
| 15.45 ( 100.0) |  5.15 (  33.3) | 15.48 ( 100.2) | Fork & Exec
|  0.73 ( 100.0) |  0.06 (   8.3) |  0.46 (  62.8) | Iterate Parameters 1; for
|  0.06 ( 100.0) |  0.01 (  17.9) |  1.67 (2983.9) | Iterate Parameters 2: while shift
```

The result `x.xx( zz.z)` indicates the average run time and the shell-run-time / bash-ran-time ratio.



## References

- [bash, ksh, zsh の速度比較 - 拡張 POSIX シェルスクリプト Advent Calendar 2013 - ダメ出し Blog](https://fumiyas.github.io/2013/12/01/benchmark.sh-advent-calendar.html)