---
title: "MrBayes - Modelos de Substituição"
linkTitle: "MrBayes - Modelos de Substituição"
weight: 4
description: >
  Codificação utilizada para informar o modelo evolutivo a ser utilizado pelo MrBayes em uma análise filogenética
---

## GTR - General Time-Reversible

#### GTR

```
lset nst=6
```

#### GTR + G

```
lset nst=6 rates=gamma
```

#### GTR + I

```
lset nst=6 rates=propinv
```

#### GTR + I + G

```
lset nst=6 rates=invgamma
```


## SYM - Symmetrical

#### SYM

```
lset nst=6
prset statefreqpr=fixed(equal)
```

#### SYM + G 

```
lset nst=6 rates=gamma
prset statefreqpr=fixed(equal)
```

#### SYM + I

```
lset nst=6 rates=propinv
prset statefreqpr=fixed(equal)
```

#### SYM + I + G 

```
lset nst=6 rates=invgamma
prset statefreqpr=fixed(equal)
```

## HKY - Hasegawa-Kishino-Yano

#### HKY

```
lset nst=2
```

#### HKY + G

```
lset nst=2 rates=gamma
```

#### HKY + I

```
lset nst=2 rates=propinv
```

#### HKY + I + G

```
lset nst=2 rates=invgamma
```

## K2P - Kimura 2-Parâmetros

#### K2P

```
lset nst=2
prset statefreqpr=fixed(equal)
```

#### K2P + G 

```
lset nst=2 rates=gamma
prset statefreqpr=fixed(equal)
```

#### K2P + I

```
lset nst=2 rates=propinv
prset statefreqpr=fixed(equal)
```

#### K2P + I + G 

```
lset nst=2 rates=invgamma
prset statefreqpr=fixed(equal)
```

## F81 - Felsenstein 1981

#### F81

```
lset nst=1
```

#### F81 + G

```
lset nst=1 rates=gamma
```

#### F81 + I

```
lset nst=1 rates=propinv
```

#### F81 + I + G

```
lset nst=1 rates=invgamma
```

## JC - Jukes Cantor

#### JC

```
lset nst=1
prset statefreqpr=fixed(equal)
```

#### JC + G 

```
lset nst=1 rates=gamma
prset statefreqpr=fixed(equal)
```

#### JC + I

```
lset nst=1 rates=propinv
prset statefreqpr=fixed(equal)
```

#### JC + I + G 

```
lset nst=1 rates=invgamma
prset statefreqpr=fixed(equal)
```