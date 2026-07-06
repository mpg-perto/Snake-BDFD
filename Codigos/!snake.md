# Comando `!snake`

> [!IMPORTANT]
> Pégalo tal cual en el editor de código de tu comando `!snake` en BDFD.

```bdscript
$nomention
$if[$getUserVar[snake_alive;$authorID]==yes]
⚠️ Ya tienes una partida en curso. Usa el botón ⏹️ de tu partida anterior para reiniciarla.
$else
$setUserVar[snake_body;3,3|3,2|3,1;$authorID]
$setUserVar[snake_dir;right;$authorID]
$setUserVar[snake_score;0;$authorID]
$setUserVar[snake_alive;yes;$authorID]


$textSplit[3,3|3,2|3,1;|]
$var[cand1;$random[1;5],$random[1;5]]
$if[$getTextSplitIndex[$var[cand1]]==-1]
$setUserVar[snake_apple;$var[cand1];$authorID]
$else
$var[cand2;$random[1;5],$random[1;5]]
$if[$getTextSplitIndex[$var[cand2]]==-1]
$setUserVar[snake_apple;$var[cand2];$authorID]
$else
$var[cand3;$random[1;5],$random[1;5]]
$if[$getTextSplitIndex[$var[cand3]]==-1]
$setUserVar[snake_apple;$var[cand3];$authorID]
$else
$if[$getTextSplitIndex[1,1]==-1]$setUserVar[snake_apple;1,1;$authorID]
$elseif[$getTextSplitIndex[1,2]==-1]$setUserVar[snake_apple;1,2;$authorID]
$elseif[$getTextSplitIndex[1,3]==-1]$setUserVar[snake_apple;1,3;$authorID]
$elseif[$getTextSplitIndex[1,4]==-1]$setUserVar[snake_apple;1,4;$authorID]
$elseif[$getTextSplitIndex[1,5]==-1]$setUserVar[snake_apple;1,5;$authorID]
$elseif[$getTextSplitIndex[2,1]==-1]$setUserVar[snake_apple;2,1;$authorID]
$elseif[$getTextSplitIndex[2,2]==-1]$setUserVar[snake_apple;2,2;$authorID]
$elseif[$getTextSplitIndex[2,3]==-1]$setUserVar[snake_apple;2,3;$authorID]
$elseif[$getTextSplitIndex[2,4]==-1]$setUserVar[snake_apple;2,4;$authorID]
$elseif[$getTextSplitIndex[2,5]==-1]$setUserVar[snake_apple;2,5;$authorID]
$elseif[$getTextSplitIndex[3,1]==-1]$setUserVar[snake_apple;3,1;$authorID]
$elseif[$getTextSplitIndex[3,2]==-1]$setUserVar[snake_apple;3,2;$authorID]
$elseif[$getTextSplitIndex[3,3]==-1]$setUserVar[snake_apple;3,3;$authorID]
$elseif[$getTextSplitIndex[3,4]==-1]$setUserVar[snake_apple;3,4;$authorID]
$elseif[$getTextSplitIndex[3,5]==-1]$setUserVar[snake_apple;3,5;$authorID]
$elseif[$getTextSplitIndex[4,1]==-1]$setUserVar[snake_apple;4,1;$authorID]
$elseif[$getTextSplitIndex[4,2]==-1]$setUserVar[snake_apple;4,2;$authorID]
$elseif[$getTextSplitIndex[4,3]==-1]$setUserVar[snake_apple;4,3;$authorID]
$elseif[$getTextSplitIndex[4,4]==-1]$setUserVar[snake_apple;4,4;$authorID]
$elseif[$getTextSplitIndex[4,5]==-1]$setUserVar[snake_apple;4,5;$authorID]
$elseif[$getTextSplitIndex[5,1]==-1]$setUserVar[snake_apple;5,1;$authorID]
$elseif[$getTextSplitIndex[5,2]==-1]$setUserVar[snake_apple;5,2;$authorID]
$elseif[$getTextSplitIndex[5,3]==-1]$setUserVar[snake_apple;5,3;$authorID]
$elseif[$getTextSplitIndex[5,4]==-1]$setUserVar[snake_apple;5,4;$authorID]
$elseif[$getTextSplitIndex[5,5]==-1]$setUserVar[snake_apple;5,5;$authorID]
$endif
$endif
$endif
$endif

$var[bodyNow;3,3|3,2|3,1]
$var[appleNow;$getUserVar[snake_apple;$authorID]]
$var[scoreNow;0]

$textSplit[$var[bodyNow];|]
$var[row1;$if[$getTextSplitIndex[1,1]==1]🟨$elseif[$getTextSplitIndex[1,1]>-1]🟩$elseif[1,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,2]==1]🟨$elseif[$getTextSplitIndex[1,2]>-1]🟩$elseif[1,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,3]==1]🟨$elseif[$getTextSplitIndex[1,3]>-1]🟩$elseif[1,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,4]==1]🟨$elseif[$getTextSplitIndex[1,4]>-1]🟩$elseif[1,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[1,5]==1]🟨$elseif[$getTextSplitIndex[1,5]>-1]🟩$elseif[1,5==$var[appleNow]]🍎$else⬛$endif]
$var[row2;$if[$getTextSplitIndex[2,1]==1]🟨$elseif[$getTextSplitIndex[2,1]>-1]🟩$elseif[2,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,2]==1]🟨$elseif[$getTextSplitIndex[2,2]>-1]🟩$elseif[2,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,3]==1]🟨$elseif[$getTextSplitIndex[2,3]>-1]🟩$elseif[2,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,4]==1]🟨$elseif[$getTextSplitIndex[2,4]>-1]🟩$elseif[2,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[2,5]==1]🟨$elseif[$getTextSplitIndex[2,5]>-1]🟩$elseif[2,5==$var[appleNow]]🍎$else⬛$endif]
$var[row3;$if[$getTextSplitIndex[3,1]==1]🟨$elseif[$getTextSplitIndex[3,1]>-1]🟩$elseif[3,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,2]==1]🟨$elseif[$getTextSplitIndex[3,2]>-1]🟩$elseif[3,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,3]==1]🟨$elseif[$getTextSplitIndex[3,3]>-1]🟩$elseif[3,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,4]==1]🟨$elseif[$getTextSplitIndex[3,4]>-1]🟩$elseif[3,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[3,5]==1]🟨$elseif[$getTextSplitIndex[3,5]>-1]🟩$elseif[3,5==$var[appleNow]]🍎$else⬛$endif]
$var[row4;$if[$getTextSplitIndex[4,1]==1]🟨$elseif[$getTextSplitIndex[4,1]>-1]🟩$elseif[4,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,2]==1]🟨$elseif[$getTextSplitIndex[4,2]>-1]🟩$elseif[4,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,3]==1]🟨$elseif[$getTextSplitIndex[4,3]>-1]🟩$elseif[4,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,4]==1]🟨$elseif[$getTextSplitIndex[4,4]>-1]🟩$elseif[4,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[4,5]==1]🟨$elseif[$getTextSplitIndex[4,5]>-1]🟩$elseif[4,5==$var[appleNow]]🍎$else⬛$endif]
$var[row5;$if[$getTextSplitIndex[5,1]==1]🟨$elseif[$getTextSplitIndex[5,1]>-1]🟩$elseif[5,1==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,2]==1]🟨$elseif[$getTextSplitIndex[5,2]>-1]🟩$elseif[5,2==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,3]==1]🟨$elseif[$getTextSplitIndex[5,3]>-1]🟩$elseif[5,3==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,4]==1]🟨$elseif[$getTextSplitIndex[5,4]>-1]🟩$elseif[5,4==$var[appleNow]]🍎$else⬛$endif$if[$getTextSplitIndex[5,5]==1]🟨$elseif[$getTextSplitIndex[5,5]>-1]🟩$elseif[5,5==$var[appleNow]]🍎$else⬛$endif]

$addContainer[snakeC;2ECC71]
$addTextDisplay[🐍 **Snake** — Jugador: $username
Puntaje: $var[scoreNow];snakeC]
$addSeparator[true;large;snakeC]
$addTextDisplay[$var[row1];snakeC]
$addTextDisplay[$var[row2];snakeC]
$addTextDisplay[$var[row3];snakeC]
$addTextDisplay[$var[row4];snakeC]
$addTextDisplay[$var[row5];snakeC]
$addSeparator[true;large;snakeC]

$addActionRow[rowUp;snakeC]
$addButtonCV2[snake-deco-1-1;;secondary;true;⬛;rowUp]
$addButtonCV2[snake-up-$authorID;;secondary;false;🔼;rowUp]
$addButtonCV2[snake-deco-1-3;;secondary;true;⬛;rowUp]

$addActionRow[rowMid;snakeC]
$addButtonCV2[snake-left-$authorID;;secondary;false;◀️;rowMid]
$addButtonCV2[snake-stop-$authorID;;danger;false;⏹️;rowMid]
$addButtonCV2[snake-right-$authorID;;secondary;false;▶️;rowMid]

$addActionRow[rowDown;snakeC]
$addButtonCV2[snake-deco-3-1;;secondary;true;⬛;rowDown]
$addButtonCV2[snake-down-$authorID;;secondary;false;🔽;rowDown]
$addButtonCV2[snake-deco-3-3;;secondary;true;⬛;rowDown]
$endif
```
