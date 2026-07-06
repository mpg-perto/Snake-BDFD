# Callback `$onInteraction`

> [!IMPORTANT]
> Pégalo tal cual en el código con el trigger `$onInteraction` (sin ID entre corchetes — debe capturar TODOS los botones del bot).

```bdscript
$nomention
$textSplit[$customID;-]
$if[$splitText[1]==snake]
$var[action;$splitText[2]]
$var[ownerID;$splitText[3]]

$if[$var[ownerID]!=$authorID]
$var[unauthorized;yes]
$else
$var[unauthorized;no]
$endif

$if[$var[unauthorized]==no]

  $if[$var[action]==restart]
  $setUserVar[snake_body;3,3|3,2|3,1;$var[ownerID]]
  $setUserVar[snake_dir;right;$var[ownerID]]
  $setUserVar[snake_score;0;$var[ownerID]]
  $setUserVar[snake_alive;yes;$var[ownerID]]

 
  $textSplit[3,3|3,2|3,1;|]
  $var[cand1;$random[1;5],$random[1;5]]
  $if[$getTextSplitIndex[$var[cand1]]==-1]
  $setUserVar[snake_apple;$var[cand1];$var[ownerID]]
  $else
  $var[cand2;$random[1;5],$random[1;5]]
  $if[$getTextSplitIndex[$var[cand2]]==-1]
  $setUserVar[snake_apple;$var[cand2];$var[ownerID]]
  $else
  $var[cand3;$random[1;5],$random[1;5]]
  $if[$getTextSplitIndex[$var[cand3]]==-1]
  $setUserVar[snake_apple;$var[cand3];$var[ownerID]]
  $else
  $if[$getTextSplitIndex[1,1]==-1]$setUserVar[snake_apple;1,1;$var[ownerID]]
  $elseif[$getTextSplitIndex[1,2]==-1]$setUserVar[snake_apple;1,2;$var[ownerID]]
  $elseif[$getTextSplitIndex[1,3]==-1]$setUserVar[snake_apple;1,3;$var[ownerID]]
  $elseif[$getTextSplitIndex[1,4]==-1]$setUserVar[snake_apple;1,4;$var[ownerID]]
  $elseif[$getTextSplitIndex[1,5]==-1]$setUserVar[snake_apple;1,5;$var[ownerID]]
  $elseif[$getTextSplitIndex[2,1]==-1]$setUserVar[snake_apple;2,1;$var[ownerID]]
  $elseif[$getTextSplitIndex[2,2]==-1]$setUserVar[snake_apple;2,2;$var[ownerID]]
  $elseif[$getTextSplitIndex[2,3]==-1]$setUserVar[snake_apple;2,3;$var[ownerID]]
  $elseif[$getTextSplitIndex[2,4]==-1]$setUserVar[snake_apple;2,4;$var[ownerID]]
  $elseif[$getTextSplitIndex[2,5]==-1]$setUserVar[snake_apple;2,5;$var[ownerID]]
  $elseif[$getTextSplitIndex[3,1]==-1]$setUserVar[snake_apple;3,1;$var[ownerID]]
  $elseif[$getTextSplitIndex[3,2]==-1]$setUserVar[snake_apple;3,2;$var[ownerID]]
  $elseif[$getTextSplitIndex[3,3]==-1]$setUserVar[snake_apple;3,3;$var[ownerID]]
  $elseif[$getTextSplitIndex[3,4]==-1]$setUserVar[snake_apple;3,4;$var[ownerID]]
  $elseif[$getTextSplitIndex[3,5]==-1]$setUserVar[snake_apple;3,5;$var[ownerID]]
  $elseif[$getTextSplitIndex[4,1]==-1]$setUserVar[snake_apple;4,1;$var[ownerID]]
  $elseif[$getTextSplitIndex[4,2]==-1]$setUserVar[snake_apple;4,2;$var[ownerID]]
  $elseif[$getTextSplitIndex[4,3]==-1]$setUserVar[snake_apple;4,3;$var[ownerID]]
  $elseif[$getTextSplitIndex[4,4]==-1]$setUserVar[snake_apple;4,4;$var[ownerID]]
  $elseif[$getTextSplitIndex[4,5]==-1]$setUserVar[snake_apple;4,5;$var[ownerID]]
  $elseif[$getTextSplitIndex[5,1]==-1]$setUserVar[snake_apple;5,1;$var[ownerID]]
  $elseif[$getTextSplitIndex[5,2]==-1]$setUserVar[snake_apple;5,2;$var[ownerID]]
  $elseif[$getTextSplitIndex[5,3]==-1]$setUserVar[snake_apple;5,3;$var[ownerID]]
  $elseif[$getTextSplitIndex[5,4]==-1]$setUserVar[snake_apple;5,4;$var[ownerID]]
  $elseif[$getTextSplitIndex[5,5]==-1]$setUserVar[snake_apple;5,5;$var[ownerID]]
  $endif
  $endif
  $endif
  $endif

  $elseif[$var[action]==stop]
  $setUserVar[snake_alive;no;$var[ownerID]]

  $else
    $if[$getUserVar[snake_alive;$var[ownerID]]==yes]

      $textSplit[$getUserVar[snake_body;$var[ownerID]];|]
      $var[headStr;$splitText[1]]
      $textSplit[$var[headStr];,]
      $var[headRow;$splitText[1]]
      $var[headCol;$splitText[2]]

      $if[$var[action]==up]
      $var[newRow;$calculate[$var[headRow]-1]]
      $var[newCol;$var[headCol]]
      $elseif[$var[action]==down]
      $var[newRow;$calculate[$var[headRow]+1]]
      $var[newCol;$var[headCol]]
      $elseif[$var[action]==left]
      $var[newRow;$var[headRow]]
      $var[newCol;$calculate[$var[headCol]-1]]
      $elseif[$var[action]==right]
      $var[newRow;$var[headRow]]
      $var[newCol;$calculate[$var[headCol]+1]]
      $endif

      $var[newHead;$var[newRow],$var[newCol]]

      $if[$or[$var[newRow]<1;$var[newRow]>5;$var[newCol]<1;$var[newCol]>5]==true]
      $setUserVar[snake_alive;no;$var[ownerID]]
      $else
        $textSplit[$getUserVar[snake_body;$var[ownerID]];|]
        $if[$getTextSplitIndex[$var[newHead]]!=-1]
        $setUserVar[snake_alive;no;$var[ownerID]]
        $else
        $setUserVar[snake_dir;$var[action];$var[ownerID]]

          $if[$var[newHead]==$getUserVar[snake_apple;$var[ownerID]]]

          $var[newBody;$var[newHead]|$getUserVar[snake_body;$var[ownerID]]]
          $setUserVar[snake_score;$calculate[$getUserVar[snake_score;$var[ownerID]]+1];$var[ownerID]]
          $setUserVar[snake_body;$var[newBody];$var[ownerID]]

          $textSplit[$var[newBody];|]
            $if[$getTextSplitLength>=25]
            $c[----- Tablero lleno: NO es game over. Se reinicia el tamaño de la serpiente pero el puntaje sigue acumulado -----]
            $setUserVar[snake_body;3,3|3,2|3,1;$var[ownerID]]
            $setUserVar[snake_dir;right;$var[ownerID]]
            $c[snake_alive se queda en "yes" -> el juego continúa. snake_score NO se toca -> sigue sumando desde donde iba.]
            $textSplit[3,3|3,2|3,1;|]
            $var[cand1;$random[1;5],$random[1;5]]
              $if[$getTextSplitIndex[$var[cand1]]==-1]
              $setUserVar[snake_apple;$var[cand1];$var[ownerID]]
              $else
              $var[cand2;$random[1;5],$random[1;5]]
                $if[$getTextSplitIndex[$var[cand2]]==-1]
                $setUserVar[snake_apple;$var[cand2];$var[ownerID]]
                $else
                $var[cand3;$random[1;5],$random[1;5]]
                  $if[$getTextSplitIndex[$var[cand3]]==-1]
                  $setUserVar[snake_apple;$var[cand3];$var[ownerID]]
                  $else
                  $if[$getTextSplitIndex[1,1]==-1]$setUserVar[snake_apple;1,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,2]==-1]$setUserVar[snake_apple;1,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,3]==-1]$setUserVar[snake_apple;1,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,4]==-1]$setUserVar[snake_apple;1,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,5]==-1]$setUserVar[snake_apple;1,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,1]==-1]$setUserVar[snake_apple;2,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,2]==-1]$setUserVar[snake_apple;2,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,3]==-1]$setUserVar[snake_apple;2,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,4]==-1]$setUserVar[snake_apple;2,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,5]==-1]$setUserVar[snake_apple;2,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,4]==-1]$setUserVar[snake_apple;3,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,5]==-1]$setUserVar[snake_apple;3,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,1]==-1]$setUserVar[snake_apple;4,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,2]==-1]$setUserVar[snake_apple;4,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,3]==-1]$setUserVar[snake_apple;4,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,4]==-1]$setUserVar[snake_apple;4,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,5]==-1]$setUserVar[snake_apple;4,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,1]==-1]$setUserVar[snake_apple;5,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,2]==-1]$setUserVar[snake_apple;5,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,3]==-1]$setUserVar[snake_apple;5,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,4]==-1]$setUserVar[snake_apple;5,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,5]==-1]$setUserVar[snake_apple;5,5;$var[ownerID]]
                  $endif
                  $endif
                $endif
              $endif
            $else
            
            $var[cand1;$random[1;5],$random[1;5]]
              $if[$getTextSplitIndex[$var[cand1]]==-1]
              $setUserVar[snake_apple;$var[cand1];$var[ownerID]]
              $else
              $var[cand2;$random[1;5],$random[1;5]]
                $if[$getTextSplitIndex[$var[cand2]]==-1]
                $setUserVar[snake_apple;$var[cand2];$var[ownerID]]
                $else
                $var[cand3;$random[1;5],$random[1;5]]
                  $if[$getTextSplitIndex[$var[cand3]]==-1]
                  $setUserVar[snake_apple;$var[cand3];$var[ownerID]]
                  $else
                  $if[$getTextSplitIndex[1,1]==-1]$setUserVar[snake_apple;1,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,2]==-1]$setUserVar[snake_apple;1,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,3]==-1]$setUserVar[snake_apple;1,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,4]==-1]$setUserVar[snake_apple;1,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[1,5]==-1]$setUserVar[snake_apple;1,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,1]==-1]$setUserVar[snake_apple;2,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,2]==-1]$setUserVar[snake_apple;2,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,3]==-1]$setUserVar[snake_apple;2,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,4]==-1]$setUserVar[snake_apple;2,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[2,5]==-1]$setUserVar[snake_apple;2,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,1]==-1]$setUserVar[snake_apple;3,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,2]==-1]$setUserVar[snake_apple;3,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,3]==-1]$setUserVar[snake_apple;3,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,4]==-1]$setUserVar[snake_apple;3,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[3,5]==-1]$setUserVar[snake_apple;3,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,1]==-1]$setUserVar[snake_apple;4,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,2]==-1]$setUserVar[snake_apple;4,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,3]==-1]$setUserVar[snake_apple;4,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,4]==-1]$setUserVar[snake_apple;4,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[4,5]==-1]$setUserVar[snake_apple;4,5;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,1]==-1]$setUserVar[snake_apple;5,1;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,2]==-1]$setUserVar[snake_apple;5,2;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,3]==-1]$setUserVar[snake_apple;5,3;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,4]==-1]$setUserVar[snake_apple;5,4;$var[ownerID]]
                  $elseif[$getTextSplitIndex[5,5]==-1]$setUserVar[snake_apple;5,5;$var[ownerID]]
                  $endif
                  $endif
                $endif
              $endif
            $endif

          $else

          $var[newBody;$var[newHead]|$getUserVar[snake_body;$var[ownerID]]]
          $textSplit[$var[newBody];|]
          $removeSplitTextElement[$getTextSplitLength]
          $var[trimmedBody;$joinSplitText[|]]
          $setUserVar[snake_body;$var[trimmedBody];$var[ownerID]]

          $endif
        $endif
      $endif
    $endif
  $endif
$endif


$var[bodyNow;$getUserVar[snake_body;$var[ownerID]]]
$var[appleNow;$getUserVar[snake_apple;$var[ownerID]]]
$var[scoreNow;$getUserVar[snake_score;$var[ownerID]]]
$var[aliveNow;$getUserVar[snake_alive;$var[ownerID]]]

$textSplit[$var[bodyNow];|]
$var[row1;$if[$getTextSplitIndex[1,1]==1]🟨$elseif[$getTextSplitIndex[1,1]>-1]🟩$elseif[1,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,2]==1]🟨$elseif[$getTextSplitIndex[1,2]>-1]🟩$elseif[1,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,3]==1]🟨$elseif[$getTextSplitIndex[1,3]>-1]🟩$elseif[1,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,4]==1]🟨$elseif[$getTextSplitIndex[1,4]>-1]🟩$elseif[1,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,5]==1]🟨$elseif[$getTextSplitIndex[1,5]>-1]🟩$elseif[1,5==$var[appleNow]]🍎$else⬛$endif]
$var[row2;$if[$getTextSplitIndex[2,1]==1]🟨$elseif[$getTextSplitIndex[2,1]>-1]🟩$elseif[2,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,2]==1]🟨$elseif[$getTextSplitIndex[2,2]>-1]🟩$elseif[2,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,3]==1]🟨$elseif[$getTextSplitIndex[2,3]>-1]🟩$elseif[2,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,4]==1]🟨$elseif[$getTextSplitIndex[2,4]>-1]🟩$elseif[2,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,5]==1]🟨$elseif[$getTextSplitIndex[2,5]>-1]🟩$elseif[2,5==$var[appleNow]]🍎$else⬛$endif]
$var[row3;$if[$getTextSplitIndex[3,1]==1]🟨$elseif[$getTextSplitIndex[3,1]>-1]🟩$elseif[3,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,2]==1]🟨$elseif[$getTextSplitIndex[3,2]>-1]🟩$elseif[3,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,3]==1]🟨$elseif[$getTextSplitIndex[3,3]>-1]🟩$elseif[3,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,4]==1]🟨$elseif[$getTextSplitIndex[3,4]>-1]🟩$elseif[3,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,5]==1]🟨$elseif[$getTextSplitIndex[3,5]>-1]🟩$elseif[3,5==$var[appleNow]]🍎$else⬛$endif]
$var[row4;$if[$getTextSplitIndex[4,1]==1]🟨$elseif[$getTextSplitIndex[4,1]>-1]🟩$elseif[4,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,2]==1]🟨$elseif[$getTextSplitIndex[4,2]>-1]🟩$elseif[4,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,3]==1]🟨$elseif[$getTextSplitIndex[4,3]>-1]🟩$elseif[4,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,4]==1]🟨$elseif[$getTextSplitIndex[4,4]>-1]🟩$elseif[4,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,5]==1]🟨$elseif[$getTextSplitIndex[4,5]>-1]🟩$elseif[4,5==$var[appleNow]]🍎$else⬛$endif]
$var[row5;$if[$getTextSplitIndex[5,1]==1]🟨$elseif[$getTextSplitIndex[5,1]>-1]🟩$elseif[5,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,2]==1]🟨$elseif[$getTextSplitIndex[5,2]>-1]🟩$elseif[5,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,3]==1]🟨$elseif[$getTextSplitIndex[5,3]>-1]🟩$elseif[5,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,4]==1]🟨$elseif[$getTextSplitIndex[5,4]>-1]🟩$elseif[5,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,5]==1]🟨$elseif[$getTextSplitIndex[5,5]>-1]🟩$elseif[5,5==$var[appleNow]]🍎$else⬛$endif]

$addContainer[snakeC;2ECC71]
$addTextDisplay[🐍 **Snake** — Jugador: <@$var[ownerID]>
Puntaje: $var[scoreNow];snakeC]
$addSeparator[true;large;snakeC]
$addTextDisplay[$var[row1];snakeC]
$addTextDisplay[$var[row2];snakeC]
$addTextDisplay[$var[row3];snakeC]
$addTextDisplay[$var[row4];snakeC]
$addTextDisplay[$var[row5];snakeC]
$addSeparator[true;large;snakeC]

$if[$var[aliveNow]==yes]
$addActionRow[rowUp;snakeC]
$addButtonCV2[snake-deco-1-1;;secondary;true;⬛;rowUp]
$addButtonCV2[snake-up-$var[ownerID];;secondary;false;🔼;rowUp]
$addButtonCV2[snake-deco-1-3;;secondary;true;⬛;rowUp]

$addActionRow[rowMid;snakeC]
$addButtonCV2[snake-left-$var[ownerID];;secondary;false;◀️;rowMid]
$addButtonCV2[snake-stop-$var[ownerID];;danger;false;⏹️;rowMid]
$addButtonCV2[snake-right-$var[ownerID];;secondary;false;▶️;rowMid]

$addActionRow[rowDown;snakeC]
$addButtonCV2[snake-deco-3-1;;secondary;true;⬛;rowDown]
$addButtonCV2[snake-down-$var[ownerID];;secondary;false;🔽;rowDown]
$addButtonCV2[snake-deco-3-3;;secondary;true;⬛;rowDown]
$else
$addActionRow[rowEnd;snakeC]
$addButtonCV2[snake-restart-$var[ownerID];Reiniciar;success;false;🔄;rowEnd]
$endif

$if[$var[unauthorized]==yes]
$sendMessage[❌ No puedes usar esta partida. Ejecuta !snake para crear la tuya.]
$endif
$endif```