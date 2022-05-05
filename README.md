# fuzzy-sinking-chair-of-vincent--Demo
my first repositotory; my first demo
---
this one is a result of my very first steps in learning kTurtle scripting language.  
it is an animation of sinking chair.
- in order to make it running you would need working kTurtle application (a part of KDE project).
- just open it and the interpreter would run it for you.

thanks to Wikipedia for an inspiration[^1] and acting character!!!

>```
>#fuzzy-sinking-chair-of-vincent--Demo_by_irulan_corrino_(inspired_by_wikipedia_article_examples)_ _
># Copyright (C) 2014  irulanCorrino
>#
>#    This program is free software: you can redistribute it and/or modify
>#    it under the terms of the GNU General Public License as published by
>#    the Free Software Foundation, either version 3 of the License, or
>#    (at your option) any later version.
>#
>#    This program is distributed in the hope that it will be useful,
>#    but WITHOUT ANY WARRANTY; without even the implied warranty of
>#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
>#    GNU General Public License for more details.
>#
>#    You should have received a copy of the GNU General Public License
>#    along with this program.  If not, see <https://www.gnu.org/licenses/>.
>#
>#_and_an_actual_engine_is_here_
>learn PhantomSink $speed, $runOnce, $flag, $flagE {
>     if $speed < 3 { return }
>     penup
>     forward $speed
>     pendown
>     visibility $speed, $runOnce
>     turnright 15 
>     if not $runOnce { $runOnce = true }
>     if not $flag { resizeIterator $speed, $flagE }
>     PhantomSink $speed / 1.02, $runOnce, $flag, $flagE
>     }
>#
>learn iPenErase $brush {
>     $solvingBrush = $brush + 2
>     penwidth $solvingBrush
>     pencolor 0, 0, 0
>     }
>learn iPenMark $brush {
>     penwidth $brush
>     pencolor 0, 255, 15
>     }
>#
>learn fuzzyChair $brush, $size {
>     iPenMark $brush
>     repeat 4 {
>          forward $size
>          turnright 90
>          }
>     forward 2 * $size
>     }
>learn fuzzyChairEraser $brush, $size {
>     iPenErase $brush
>     backward 2 * $size
>     repeat 4 {
>          forward $size
>          turnright 90
>          }
>     }
>learn iObject $size, $runOnce {
>     $brush = $size / 10
>     if $brush > 1 { $brush = $brush - 1 }
>     fuzzyChair $brush, $size
>     wait 0.2
>     fuzzyChairEraser $brush, $size
>     }
>learn visibility $speed, $runOnce {
>     if not $runOnce { $size = ( 2 * $speed ) + $speed }
>      else { $size = ( ( 2 * $speed ) + $speed ) - (1 / $speed) }
>     iObject $size, $runOnce
>     }
>#
>learn resizeIterator $speed, $flagE {
>     $modifier = 1
>     $value = round $speed
>     $iterator = mod $value, 15
>     if $value < 50 { $modifier = mod $value, 5 }
>     if not $iterator or not $modifier {
>      $standardView = 2 * ( ($speed / 4) + (12 * $speed) / 3.1416 + 5 )
>      clear
>      canvassize 2 * $standardView, 2 * $standardView
>      if $flagE {
>       center
>       backward $speed * 2 + $speed + $speed / 2 + $speed / 4
>       }
>       else {
>         go ($standardView / 2 + $standardView / 4 + $standardView / 8 + $standardView / 16) , ($standardView - $standardView / 32 )
>         backward $speed + $speed / 2 + $speed / 4 + $speed / 8
>         }
>      }
>     }
>#
>learn decision {
>     message "if you prefer to calculate less (true or false)#"
>     $flagString = ask "* choose an engine to make a chair to stay at focus babes *"
>     if $flagString == "true" { $flagE = true }
>      else {
>        if $flagString == "false" { $flagE = false }
>         else {
>           if $flagString == 1 { $flagE = true }
>            else { $flagE = false }
>           }
>        }
>     return $flagE
>     }
>learn tragedy $flagE, $flag, $speed {
>     $runOnce = false 
>     $speed = $speed * 300
>     reset
>     spritehide
>     $standard = 2 * ( ($speed / 4) + (12 * $speed) / 3.1416 + 5 )
>     canvassize 2 * $standard, 2 * $standard
>     canvascolor 0, 0, 0
>     go $standard / 6 , $standard
>     PhantomSink $speed, $runOnce, $flag, $flagE
>     }
>learn container {
>     $flag = true
>     message "answer with a number#bigger_then_1 (integer and positive please) (one is a sufficient value)"
>     $speed = ask "* curtains are ready to eat you babes *"
>     message "#it is needed to disagree (true or false)"
>     $flagString = ask "* we can resist to a temptation to pursuit a chair *"
>     if $flagString == "true" { $flag = true }
>      else {
>        if $flagString == "false" { $flag = false }
>         else {
>           if $flagString == 1 { $flag = true }
>            else { $flag = false }
>           }
>        }
>     $flagE = false
>     if not $flag { $flagE = decision }
>     tragedy $flagE, $flag, $speed
>     }
>#
>container
>#
>```

[^1]: cannot provide you with the link because i've lost my memory (...partially)
