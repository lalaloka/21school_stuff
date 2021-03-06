1
00:00:06,823 --> 00:00:08,123
Hello once again!

2
00:00:08,123 --> 00:00:09,223
We're going to conclude

3
00:00:09,223 --> 00:00:10,343
this "pointers day"

4
00:00:10,343 --> 00:00:11,943
with pointers' usage.

5
00:00:11,943 --> 00:00:13,323
So far, we've only

6
00:00:13,323 --> 00:00:14,563
played with pointers

7
00:00:14,563 --> 00:00:16,543
within a main, or a function

8
00:00:16,543 --> 00:00:18,653
and you probably don't see the point.

9
00:00:18,653 --> 00:00:20,993
But as soon as you'll know how to allocate memory,

10
00:00:21,013 --> 00:00:22,703
you'll understand their importance.

11
00:00:22,703 --> 00:00:24,233
Because so far,

12
00:00:24,233 --> 00:00:25,773
we've named things on the stack.

13
00:00:25,773 --> 00:00:27,393
Every time we have a variable "a",

14
00:00:27,393 --> 00:00:29,393
and a variable "b", we get their addresses.

15
00:00:29,393 --> 00:00:31,103
That's too bad,

16
00:00:31,103 --> 00:00:32,833
because we only know where they are

17
00:00:32,833 --> 00:00:35,253
but soon, we'll be able to say

18
00:00:35,253 --> 00:00:36,943
"Hello, gimme some memory"

19
00:00:36,943 --> 00:00:39,253
without having to name them.

20
00:00:39,253 --> 00:00:41,143
That's where pointers come into play.

21
00:00:41,143 --> 00:00:42,673
Here's a simple example

22
00:00:42,673 --> 00:00:44,243
of pointer usage,

23
00:00:44,243 --> 00:00:46,443
that'll be extremely useful

24
00:00:46,443 --> 00:00:47,993
for today's lesson.

25
00:00:49,063 --> 00:00:50,773
We have a function, a main, rather,

26
00:00:50,782 --> 00:00:52,952
and a function fct().

27
00:00:53,394 --> 00:00:55,154
In my main, I've declared an int "a",

28
00:00:55,154 --> 00:00:57,404
with the value "42".

29
00:00:57,404 --> 00:00:59,524
Then I called my function fct(),

30
00:00:59,524 --> 00:01:01,784
with "a" as a parameter.

31
00:01:02,055 --> 00:01:03,855
Then I'll display "a"'s value

32
00:01:03,855 --> 00:01:05,285
in my main,

33
00:01:06,063 --> 00:01:07,933
then display a "\n" and return 0.

34
00:01:09,802 --> 00:01:11,642
What will my function fct() do?

35
00:01:11,642 --> 00:01:13,552
It takes an int as parameter,

36
00:01:13,552 --> 00:01:15,012
that we've called "a",

37
00:01:15,012 --> 00:01:17,132
and I'll set its value to 12.

38
00:01:17,223 --> 00:01:18,833
What do you think will happen

39
00:01:18,833 --> 00:01:20,383
when I execute this program?

40
00:01:20,383 --> 00:01:22,193
What will be displayed?

41
00:01:22,193 --> 00:01:22,943
12 or 42?

42
00:01:25,272 --> 00:01:26,212
Let's test this...

43
00:01:28,092 --> 00:01:30,232
You'll never be able to break the machine,

44
00:01:30,232 --> 00:01:31,852
so don't hesitate to run tests.

45
00:01:32,332 --> 00:01:33,322
42 is displayed.

46
00:01:33,772 --> 00:01:35,232
Let's go back to our code.

47
00:01:37,793 --> 00:01:39,593
"a", here, is the "a" from my main.

48
00:01:39,593 --> 00:01:40,423
Its value is 42.

49
00:01:41,582 --> 00:01:43,982
Know that by passing a parameter,

50
00:01:44,998 --> 00:01:46,838
we always pass it "by copy"...

51
00:01:47,042 --> 00:01:48,912
Basically, here I didn't pass "a",

52
00:01:48,912 --> 00:01:50,952
but a copy of "a"'s value.

53
00:01:52,163 --> 00:01:53,383
So the "a" that's here,

54
00:01:53,383 --> 00:01:56,153
is not the same. It's my function's "a".

55
00:01:56,153 --> 00:01:57,943
So here, the "a" possesses a copy

56
00:01:57,943 --> 00:02:00,033
of the first "a", that's in my main.

57
00:02:00,533 --> 00:02:03,293
Therefore, it took the value of "42".

58
00:02:04,513 --> 00:02:07,133
When I modify this, "a = 12",

59
00:02:07,253 --> 00:02:09,283
I'm modifying the "a" from my function.

60
00:02:09,283 --> 00:02:11,053
But the "a" from my main

61
00:02:11,053 --> 00:02:12,203
hasn't changed!

62
00:02:13,403 --> 00:02:14,843
Once again, we did not pass it

63
00:02:14,843 --> 00:02:16,033
the "a" from my main,

64
00:02:16,033 --> 00:02:17,853
we passed it a copy of its value.

65
00:02:17,853 --> 00:02:19,633
So how can we manage,

66
00:02:19,633 --> 00:02:20,793
in my function,

67
00:02:20,793 --> 00:02:23,163
to modify the value of "a" in my main?

68
00:02:23,163 --> 00:02:24,873
Well, instead of copying

69
00:02:24,873 --> 00:02:26,013
the value of "a",

70
00:02:26,013 --> 00:02:27,893
I'm going to copy the address of "a".

71
00:02:29,403 --> 00:02:31,283
And here, instead of having an int,

72
00:02:31,302 --> 00:02:32,842
otherwise, it won't compile,

73
00:02:32,842 --> 00:02:34,692
as I'm passing it an int's address,

74
00:02:34,692 --> 00:02:36,372
so here, we'd need to turn it

75
00:02:36,372 --> 00:02:38,022
into a pointer to int.

76
00:02:38,022 --> 00:02:40,202
My "a" becomes a pointer to int,

77
00:02:40,202 --> 00:02:42,552
and if I want to change the value of "a",

78
00:02:42,552 --> 00:02:44,392
so the value pointed by

79
00:02:44,392 --> 00:02:45,712
my function's "a",

80
00:02:45,712 --> 00:02:47,832
I'm going to have to dereference here.

81
00:02:50,423 --> 00:02:51,853
Normally, if you've watched

82
00:02:51,853 --> 00:02:53,063
the other videos,

83
00:02:53,063 --> 00:02:54,433
this notion should be clear.

84
00:02:55,152 --> 00:02:56,492
So I'm calling my function,

85
00:02:56,492 --> 00:02:57,942
by passing the address of "a",

86
00:02:57,942 --> 00:02:59,892
so made a copy of the address of "a"

87
00:02:59,892 --> 00:03:01,442
which goes into a pointer to int

88
00:03:01,442 --> 00:03:02,862
also called "a",

89
00:03:02,862 --> 00:03:04,062
(just to confuse you)

90
00:03:04,062 --> 00:03:05,592
then I've decided that the value

91
00:03:05,592 --> 00:03:06,592
pointed by this "a",

92
00:03:06,592 --> 00:03:08,492
would take the value 12.

93
00:03:09,003 --> 00:03:10,603
Let's see what happens.

94
00:03:15,103 --> 00:03:15,863
Here we go!

95
00:03:15,863 --> 00:03:17,863
It now has 12 for value!

96
00:03:19,843 --> 00:03:21,383
The purpose of pointers

97
00:03:21,383 --> 00:03:25,383
is to be able to either move around an array,

98
00:03:26,043 --> 00:03:29,223
either move around a character string,

99
00:03:29,653 --> 00:03:31,723
(which is an array of "char"s)

100
00:03:33,223 --> 00:03:38,433
either pass a variable's address

101
00:03:38,433 --> 00:03:40,363
and modify it in a function.

102
00:03:40,502 --> 00:03:44,232
That's one of the most common use of pointers.

103
00:03:46,703 --> 00:03:50,703
This concludes our lesson on pointers.

104
00:03:50,703 --> 00:03:52,423
If you struggle with these notions,

105
00:03:52,423 --> 00:03:54,643
don't hesitate to watch these videos again

106
00:03:54,643 --> 00:03:56,523
but mostly, try it out for yourselves.

107
00:03:56,523 --> 00:03:58,813
As I've said before, you can't break the machine.

108
00:03:58,813 --> 00:04:00,483
read error messages,

109
00:04:00,483 --> 00:04:02,343
the compiler is here to help.

110
00:04:02,343 --> 00:04:03,933
Good day and good luck.

> Buna ziua din nou. 

> Vom termina ziua despre pointeri cu aspecte legate de utilizarea lor. 

> Pentru ca pana acum ne-am jucat cu pointerii in interiorul unei functii "main" si probabil ca inca nu vedeti adevarata miza. 

> Veti incepe sa intelegeti miza in continuare, de indata ce veti putea aloca memorie. 

> Pana acum am utilizat stiva de memorie, de fiecare data aveam variabile numite "a”, "b", etc., recuperam adresa lor, cunoasteam in mare zona de memorie in care erau salvate. 

> In curand o sa vedeti ca putem aloca memorie, fara sa stim in ce zona de memorie este facuta alocarea si aici vor interveni pointerii. 

> lata un exemplu simplu de utilizare a pointerilor care ne va fi util astazi. 

> Avem o functie "main" si o functie "fct". 

> In functia "main" am declarat o variabila "a" de tip "int" si i-am dat valoarea 42. 

> Apoi am apelat functia "fct" cu parametrul 

> In functia "main", voi afisa apoi valoarea "a" si un retur la linie ('\n').

> Functia "fct" ia un parametru de tip "int" pe care l-am numit tot "a" (ca sa va incurc), si ii da valoarea 12. 

> Dupa parerea voastra ce se va afisa pe ecran: 12 sau 42? 

> Cel mai bun mod... Nu puteti sa "stricati" calculatorul, deci nu ezitati sa testati. 

> Se afîseaza 42.. 

> Voi reveni in cod. Afisam 42... Uitati-va aici: variabila "a" din functia "main" are valoarea 42. 

> Atunci cand apelam o functie, transmitem parametri prin copiere. Deci nu am transmis "a”, ci o copie a valorii lui "a". 

> Parametrul "a" din functia "fct" e o copie a celui din "main", deci doar primeste valoarea 42. 

> Cand modific "a"-ul de aici, dandu-i valoarea 12, e vorba de "a"-ul din functie. 

> Dar "a"-ul din "main" nu s-a schimbat. 

> Inca o data, nu am transmis "a"-ul din main, am trasmis o copie a valorii lui. 

> Cum facem ca sa modificam valoarea variabilei "a" din functia "main" folosind functia "fct"? 

> In loc sa transmitem valoarea lui "a", vom transmite adresa lui "a". 

> Si aici, functia "fct" va primi ca parametru un pointer la "int" in loc de un simplu "int". 


> devenit pointer catre "int", si daca vreau sa modici valoarea "a"-ului din functie, trebuie sa-l dereferentiez aici. 

> Daca ati urmarim videoclipurile anterioare de astazi, ar trebui sa fie clar. 

> Apelez functia "fct" transmitand o copie a adresei lui "a" printr-un pointer la "int" (caruia ii spun tot "a", ca sa va incurc). 

> Am facut astfel incat la adresa spre care pointeaza pointerul "a" sa salvam valoarea 12. 

> Sa vedem ce obtinem... 

> Acum avem valoarea 12. 

> Putem folosi un pointer fie pentru a ne deplasa intr-un tablou sau intr-un sir de caractere (care e un tablou de "char"), 

> fie pentru a transmite adresa unei variabile si a o modifica intr-o functie. 

> Aceasta din urma este una dintre formele cele mai frecvent utilizate pentru pointeri. 

> Concluzionam aici cursul de pointeri de astazi. 

> Daca aveti neclaritati, nu ezitati sa urmariti din nou toate cursurile de astazi, dar mai ales, nu ezitati sa incercati voi insiva. 

> Sa nu va fie frica de faptul ca ati putea strica computerul. Si analizati atent mesajele de eroare. Compilatorul a fost facut sa va ajute. 

> Va urez o zi buna si mult curaj.