# fpconf2016

Название доклада:

LiquidHaskell: изящные типы

Суть:

Все мы любим Haskell за его выразительную систему типов, избавляющую нас от множества проблем. Но нельзя ли сделать наши типы ещё более впечатляющими? LiquidHaskell, статический верификатор Haskell-кода, предлагает нам свой ответ на этот вопрос. В докладе будут рассмотрены основы работы с LiquidHaskell, и вместе мы попытаемся понять, нужен ли нам этот инструмент.

0. Исследовательский проект Калифорнийского университета.
1. Устанавливаем пакет liquidhaskell, через stack.
2. В результате - две команды, liquid и lhi.
3. Для работы нужен пакет z3, доказатель теорем от Microsoft Research, живёт в линуксовых репозиториях и в homebrew.
3. liquid src/Main.hs выдаёт обычные GHC-подобные ошибки, но в куда лучшем виде.

[1 of 1] Compiling Main             ( src/Main.hs, .stack-work/dist/x86_64-linux/Cabal-1.22.5.0/build/learnHaskell/learnHaskell-tmp/Main.o )

/home/dshevchenko/learnHaskell/src/Main.hs:8:16: Not in scope: ‘f’

---

Invalid Source


 src/Main.hs:8:16: Error: GHC Error
  
   8 | main = print $ f "Hi!"
                      ^
                        
       Not in scope: ‘f’

4. идея - улучшенный тип

type Positive = {v:Int | 0 < v}



