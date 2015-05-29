# pussy lang

#### Синтаксис:
    letter      = "A"|..|"Z"|"a"|..|"z"
    digit       = "0"|..|"9"
    ident       = letter {letter|digit}
    integer     = digit {digit}
    vardecl     = ident "=" integer "\n"
    varlist     = vardecl {vardecl}
    prccall     = ident "\n"
    assigment   = ident "=" (integer | ident) "\n"
    ifstatement = ident "#" (integer | ident) [ident] "\n"
    statement   = prccall | assigment | ifstatement
    sequence    = statement { statement}
    prcdecl     = ident ":" "\n" sequence
    prclist     = prcdecl {prcdecl}
    program     = varlist prclist

#### Пример:
    arg1 = 2
    arg2 = 2
    tmp1 = 0
    res1 = 0
    inc:
      res1
      tmp1
      tmp1 # arg2
      tmp1 = 0
    sum:
      res1 = arg1
      tmp1 # arg2 inc
    main:
      sum

#### Семантика:
1. Выполнение алгоритма начинается с вызова последней процедуры (см. `main`)
2. Вызов переменной по имени означает инкремент оной (см. первые два оператора в процедуре `inc`)
3. `tmp1 # arg2 inc` - означает вызов процедуры `inc` если `tmp1` не равно `arg2`
4. Условие без указания процедуры означает рекурсивный вызов
