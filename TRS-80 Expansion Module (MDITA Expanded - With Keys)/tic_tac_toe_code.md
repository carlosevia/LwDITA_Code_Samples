---
id: tic_tac_toe_code
shortdesc: Enter this BASIC code into your [computer_model] in order to play a game of tic-tac-toe.
author: Thomas Price
---

# Tic-Tac-Toe Code

```
10 ' COPYRIGHT 1978 THOMAS D. PRICE, JR.
30 RANDOM
  : CLS
  : PRINT
  : PRINT
  : PRINT CHR$(23); TAB(8) "TIC-TAC-TOE"
  : PRINT TAB(8) STRING$(11, CHR$(131))
  : PRINT
40 PRINT "HERE'S YOUR CHANCE TO PLAY"
  : PRINT "TIC-TAC-TOE AGAINST THE TRS-8O."
  : PRINT "THE COMPUTER PLAYS A VERY TOUGH"
  : PRINT "GAME AND WILL BE DIFFICULT TO"
  : PRINT "DEFEAT. IT CAN BE DONE, BUT NOT"
  : PRINT "EASILY AND NOT EVERY TIME!"
  : PRINT
50 PRINT "JUST TAP THE SPACE BAR WHEN"
  : PRINT "YOU'RE READY TO START."
60 c$ = INKEY$
  : IF c$ <> " " THEN 60
130 q$ = "N"
  : CLS
  : PRINT CHR$(23);
  : PRINT@ 20, "TIC-TAC-TOE"
140 FOR i = 1 TO 9
  : a(i) = 1
  : NEXT i
150 PRINT@ 212, 1;
  : PRINT@ 222, 2;
  : PRINT@ 232, 3;
  : PRINT@ 404, 8;
  : PRINT@ 414, 9;
  : PRINT@ 424, 4;
  : PRINT@ 596, 7;
  : PRINT@ 606, 6;
  : PRINT@ 616, 5;
160 FOR y = 6 TO 34
  : SET(52, y)
  : SET(72, y)
  : NEXT
  : FOR x = 33 TO 89
  : SET(x, 15)
  : SET(x, 25)
  : NEXT
180 PRINT@ 832, "WOULD YOU LIKE TO GO FIRST?"
190 r$ = INKEY$
  : IF r$ = "Y" THEN GOSUB 720
  : GOTO 210 ELSE IF r$ = "N" THEN GOSUB 720
  : GOTO 200 ELSE 190
200 m = RND(5) * 2 - 1
  : GOSUB 680
210 GOSUB 610
220 m = 9
  : IF a(9) = 1 THEN 240
230 m = RND(4) * 2 - 1
  : IF a(m) < 1 THEN 230
240 GOSUB 680
250 GOSUB 610
255 IF q$ <> "N" THEN 130
260 GOSUB 320
265 IF q$ <> "N" THEN 130
270 GOTO 250
280 GOSUB 720
  : PRINT "THE GAME IS A DRAW !!"
290 PRINT "WOULD YOU LIKE TO TRY AGAIN?"
300 q$ = INKEY$
  : IF q$ = "Y" THEN RETURN ELSE IF q$ = "N" THEN 310 ELSE 300
310 CLS
  : PRINT CHR$(23)
  : PRINT@ 460, "GOODBYE FOR NOW"
  : PRINT
  : PRINT
315 END
320 c = 1
330 READ h, j, k
  : IF h = 0 THEN 390
340 m = k
  : IF (a(h) = 0) * (a(j) = 0) * (a(k) = 1) THEN 380
350 m = h
  : IF (a(h) = 1) * (a(j) = 0) * (a(k) = 0) THEN 380
360 m = j
  : IF (a(h) = 0) * (a(j) = 1) * (a(k) = 0) THEN 380
370 c = c + 1
  : GOTO 330
380 RESTORE
  : GOSUB 690
  : PRINT "GOTCHA!! I WIN!!"
  : GOTO 810
390 RESTORE
400 READ h, j, k
  : IF h = 0 THEN 480
410 m = k
  : IF (a(h) = -1) * (a(j) = -1) * (a(k) = 1) THEN 450
420 m = h
  : IF (a(h) = 1) * (a(j) = -1) * (a(k) = -1) THEN 450
430 m = j
  : IF (a(h) = -1) * (a(j) = 1) * (a(k) = -1) THEN 450
440 GOTO 400
450 RESTORE
  : GOSUB 680
  : FOR i = 1 TO 9
  : IF a(i) = 1 THEN 470
460 NEXT i
  : GOTO 280
470 RETURN
480 RESTORE
490 FOR i = 1 TO 7 STEP 2
  : IF a(i) < 1 THEN 510
500 NEXT i
  : z = 7
  : IF (a(2) = -1) * (a(4) = -1) THEN 504
501 z = 1
  : IF (a(4) = -1) * (a(6) = -1) THEN 504
502 z = 3
  : IF (a(6) = -1) * (a(8) = -1) THEN 504
503 z = 5
504 m = RND(4) * 2 - 1
  : IF m = z THEN 504
505 GOSUB 680
  : RETURN
510 READ h, j, k
  : IF h = 0 THEN 590
520 IF (a(h) = -1) + (a(j) = -1) + (a(k) = -1) THEN 510
530 IF (a(h) = 1) * (a(j) = 1) * (a(k) = 1) THEN 510
535 IF a(9) = -1 THEN 550
540 t = RND(2)
  : ON t GOTO 550, 560
550 m = h
  : IF a(m) = 1 GOTO 580
560 m = k
  : IF a(m) = 1 GOTO 580
570 m = j
580 RESTORE
  : GOSUB 680
  : RETURN
590 RESTORE
600 GOTO 280
610 PRINT "WHAT IS YOUR MOVE?";
615 m$ = INKEY$
  : IF m$ = "" THEN 615 ELSE IF (ASC(m$) > 48) AND (ASC(m$) < 58) THEN m = VAL(m$)
  : GOTO 620 ELSE 615
620 PRINT m
  : FOR t = 1 TO 200
  : NEXT
  : IF a(m) = 1 THEN 640
630 GOSUB 720
  : PRINT "SORRY! "; m; "HAS BEEN USED!"
  : FOR t = 1 TO 2500
  : NEXT
  : GOSUB 720
  : GOTO 610
640 a(m) = -1
  : GOSUB 730
650 w = y
  : v = y + 4
  : FOR z = x TO x + 8 STEP 4
  : IF z = x SET(z, w)
  : SET(z, v)
  : w = w + 1
  : v = v - 1 ELSE SET(z - 1, w)
  : SET(z - 1, v)
  : w = w + 1
  : v = v - 1
  : SET(z, w)
  : SET(z, v)
  : w = w + 1
  : v = v - 1
660 NEXT
670 GOSUB 720
  : GOSUB 740
  : RETURN
680 PRINT "HERE IS MY MOVE"
  : a(m) = 0
690 GOSUB 730
695 FOR d = 1 TO 200
  : NEXT d
700 FOR z = y TO y + 4
  : SET(x, z)
  : SET(x + 8, z)
  : NEXT z
710 FOR z = x TO x + 8
  : SET(z, y)
  : SET(z, y + 4)
  : NEXT z
715 FOR d = 1 TO 200
  : NEXT d
720 PRINT@ 832, CHR$(31);
  : PRINT@ 832, ;
  : RETURN
730 ON m GOTO 731, 732, 733, 734, 735, 736, 737, 738, 739
731 x = 37
  : y = 8
  : RETURN
732 x = 57
  : y = 8
  : RETURN
733 x = 77
  : y = 8
  : RETURN
734 x = 77
  : y = 18
  : RETURN
735 x = 77
  : y = 28
  : RETURN
736 x = 57
  : y = 28
  : RETURN
737 x = 37
  : y = 28
  : RETURN
738 x = 37
  : y = 18
  : RETURN
739 x = 57
  : y = 18
  : RETURN
740 c = 1
750 READ h, j, k
  : IF h = 0 THEN 790
760 IF (a(h) = -1) * (a(j) = -1) * (a(k) = -1) THEN 800
780 c = c + 1
  : GOTO 750
790 RESTORE
  : RETURN
800 RESTORE
  : GOSUB 820
  : PRINT "VERY GOOD !! YOU WIN !!"
  : GOTO 290
810 GOSUB 820
  : GOTO 290
820 ON c GOTO 821, 822, 823, 824, 825, 826, 827, 828
821 FOR x = 32 TO 92
  : SET(x, 10)
  : NEXT
  : RETURN
822 FOR y = 5 TO 35
  : SET(81, y)
  : NEXT
  : RETURN
823 FOR x = 32 TO 92
  : SET(x, 30)
  : NEXT
  : RETURN
824 FOR y = 5 TO 35
  : SET(41, y)
  : NEXT
  : RETURN
825 FOR y = 5 TO 35
  : SET(61, y)
  : NEXT y
  : RETURN
826 FOR x = 32 TO 92
  : SET(x, 20)
  : NEXT
  : RETURN
827 y = 5
  : FOR x = 32 TO 92 STEP 4
  : SET(x, y)
  : SET(x + 1, y + 1)
  : y = y + 2
  : NEXT
  : RETURN
828 y = 35
  : FOR x = 32 TO 92 STEP 4
  : SET(x, y)
  : SET(x + 1, y - 1)
  : y = y - 2
  : NEXT
  : RETURN
829 DATA 1,2,3,3,4,5,5,6,7,7,8,1,2,9,6,8,9,4,1,9,5,3,9,7,0,0,0
```
<!-- This code has been released under a Creative Commons CC0 1.0 Universal license. -->
<!-- The person who associated a work with this deed has dedicated the work to the public domain by waiving all of his or her rights to the work worldwide under copyright law, including all related and neighboring rights, to the extent allowed by law. -->