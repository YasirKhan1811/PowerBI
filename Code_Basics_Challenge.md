# Code Basics Challenge
---

Formula to show change w.r.t previous month:
```PBI
Description = 
              VAR 
                  _difference = SUM(sales) - [previous day]
                  
              VAR
                  _direction = 
                         SWITCH(
                              True()
                              , _difference > 0, "^"
                              , _difference < 0, "v"
                              , "."
                              ,
                              )
              VAR
                 _pecentchange = 
                              _difference/[previous day]
                  Return 
                        _direction & " " & FORMAT(_pecentchange, '##.##%') & " (" & _difference & ")"   
                            
```                  

Formula for coloring:
```PBI
Description color = 
                   VAR 
                      _difference = SUM(sales) - [previous day]
                   Return
                   SWITCH(
                          True()
                          , _difference > 0, "green"
                          , _difference < 0, "red"
                          , "black",
                          )
```
