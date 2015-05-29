# pussy lang

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
