# LL(1) Parser
C implementation of LL(1) Parser.

## What is Parser?
The parser is that phase of the compiler which takes a token string as input and with the help of existing grammar, converts it into the corresponding Intermediate Representation. The parser is also known as Syntax Analyzer.

## Types of Parser
- Top-Down Parser: The Top-Down Parser is the parser that generates parse for the given input string with the help of grammar productions by expanding the non-terminals i.e. it starts from the start symbol and ends on the terminals. It uses left most derivation. 

- Bottom-Up Parser: The Bottom-Up Parser is the parser that generates the parse tree for the given input string with the help of grammar productions by compressing the non-terminals i.e. it starts from non-terminals and ends on the start symbol. It uses the reverse of the rightmost derivation. 

## LL(1) Parser

A top-down parser that uses a one-token lookahead is called an **LL(1) parser**.

* The first L indicates that the input is read from left to right.
* The second L says that it produces a left-to-right derivation.
* And the 1 says that it uses one lookahead token.

## Important Points regarding our project
* Epsilon is represented by '#'.
* Productions are of the form A=B , where 'A' is a single Non-Terminal and 'B' can be any combination of Terminals and Non- Terminals.
* The L.H.S. of the first production rule is the start symbol.
* Grammer is not left recursive.
* Each production of a non terminal is entered on a different line.
* Only Upper Case letters are Non-Terminals and everything else is a terminal.
* Do not use '!' or '$' as they are reserved for special purposes.
* All input Strings have to end with a '$'.

## Installation and Quick Start

```
  $ git clone https://github.com/srijarkoroy/Mini-LL1-Parser
  
  $ cd Mini-LL1-Parser
  
  $ gcc parser.c
  
  $ ./a.out
```

## Results

```
How many productions ? :8

Enter 8 productions in form A=B where A and B are grammar symbols :

E=TR

R=+TR

R=#

T=FY

Y=*FY

Y=#

F=(E)

F=i
```

```
----------------------------------------------
 First(E)= { (, i, }

 First(R)= { +, #, }

 First(T)= { (, i, }

 First(Y)= { *, #, }

 First(F)= { (, i, }

-----------------------------------------------

 Follow(E) = { $, ),  }

 Follow(R) = { $, ),  }

 Follow(T) = { +, $, ),  }

 Follow(Y) = { +, $, ),  }

 Follow(F) = { *, +, $, ),  }
 ```
 


                              The LL(1) Parsing Table for the above grammer :-
                             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

      ======================================================================================================
              |       +               *               (               )               i               $
      ======================================================================================================
         E    |                                       E=TR                            E=TR
      ------------------------------------------------------------------------------------------------------
         R    |       R=+TR                                           R=#                             R=#
      ------------------------------------------------------------------------------------------------------
         T    |                                       T=FY                            T=FY
      ------------------------------------------------------------------------------------------------------
         Y    |       Y=#             Y=*FY                           Y=#                             Y=#
      ------------------------------------------------------------------------------------------------------
         F    |                                       F=(E)                           F=i
      ------------------------------------------------------------------------------------------------------


Please enter the desired INPUT STRING = i+i*i$

                    ===========================================================================
                            Stack                   Input                   Action
                    ===========================================================================
                            $E                      i+i*i$                  E=TR
                            $RT                     i+i*i$                  T=FY
                            $RYF                    i+i*i$                  F=i
                            $RYi                    i+i*i$                  POP ACTION
                            $RY                     +i*i$                   Y=#
                            $R                      +i*i$                   R=+TR
                            $RT+                    +i*i$                   POP ACTION
                            $RT                     i*i$                    T=FY
                            $RYF                    i*i$                    F=i
                            $RYi                    i*i$                    POP ACTION
                            $RY                     *i$                     Y=*FY
                            $RYF*                   *i$                     POP ACTION
                            $RYF                    i$                      F=i
                            $RYi                    i$                      POP ACTION
                            $RY                     $                       Y=#
                            $R                      $                       R=#
                            $                       $                       POP ACTION

            =======================================================================================
                                            YOUR STRING HAS BEEN ACCEPTED !!
            =======================================================================================
            
## Output
![firstfollow](https://user-images.githubusercontent.com/66861242/164972224-1cc80ae9-d10d-433a-b6cf-7d20e0e7e760.png)

![parsing_table](https://user-images.githubusercontent.com/66861242/164972228-1158ed86-360a-4410-adf5-c22d66bbf0c6.png)

## Contributors
- [Rahul Anand](https://github.com/CrAzYJOKR)
- [Indira Dutta](https://github.com/indiradutta)
- [Srijarko Roy](https://github.com/srijarkoroy)
