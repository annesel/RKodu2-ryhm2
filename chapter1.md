---
title       : Andmete importimine
description : Esimene teema - andmete viimine R-i
--- type:NormalExercise lang:r xp:100 skills:3 key:2c2b6bf80e
## Andmete import 1


Andmete impordiks tekstifailist saab kasutada käsku `read.table()`. 

Funktsiooni `read.table()` argumentide abil saab paika panna, mis on imporditavas failis veergude eraldaja, mis sümbolit kasutatakse kümnendkoha määramisel, kas veergudel on olemas nimed jne.



*** =instructions

- **Ülesanne 1** Kasutades käsku `read.table()` impordi R-i fail *katsed.txt* aadressilt  *http://kodu.ut.ee/~annes/R/katsed.txt*, omista andmestik muutujale `andmed1`. Prindi andmestik ekraanile
- **Ülesanne 2** Vaata andmestiku struktuuri käsuga `str()`.


*** =hint
- Ava fail brauseri aknas ja vaata, mis on veergude eraldaja.
- Imporditud andmetabelis peab olema 6 vaatlust ja 3 tunnust.


*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Ülesanne 1: Impordi andmed, moodustades objekti andmed1. Prindi saadud objekt ekraanile
andmed1 <- read.table(_________________________________)



# Ülesanne 2: Vaata andmestiku struktuuri


 

```

*** =solution
```{r}
# Ülesanne 1: Impordi andmed, moodustades objekti andmed1. Prindi saadud objekt ekraanile
andmed1 <- read.table("http://kodu.ut.ee/~annes/R/katsed.txt", header = T, sep = "\t")
andmed1


# Ülesanne 2: Vaata andmestiku struktuuri
str(andmed1)



```

*** =sct
```{r}
# 1
test_function(name = "read.table",
              args = c("header", "sep"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `read.table`",
             args_not_specified_msg = paste("Määra `read.table` käsus argumendi", c("`header`", "`sep`" ), "väärtus."),
             incorrect_msg = paste("Oled funktsioonis `read.table` andnud vale väärtuse argumendile",  c("`header`", "`sep`"))) 
 




test_data_frame("andmed1",  
                columns = c("siin.veerus..on.lause",  "uuritavate.identifikaator..see.on.nagu.nimi", "esimesel.katsel.saadud.tulemus..katse.toimus.hommikul.kell.8.30"),
                eq_condition = "equivalent",
                undefined_msg = "Andmestik `andmed1` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `andmed1`.",
                incorrect_msg = "Objekti `andmed1` väärtus ei ole korrektne. Proovi uuesti.") 
 
 
#test_object("andmed1",  
#%            undefined_msg = "Objekt `andmed1` on defineerimata.",
#            incorrect_msg = "Objekti `andmed1` väärtus ei ole korrektne. Proovi uuesti.") 
 
 
 
 
 
test_output_contains(expr = "andmed1",
                     times = 1,
                     incorrect_msg = "Andmestik on ekraanile printimata")
 
 


# 2
test_function_result(name = "str",
                     index = 1,
                     eq_condition = "equivalent",
                     not_called_msg = "Teises ülesandes pead kasutama funktsiooni `str`",
                     error_msg = "Teises ülesandes on midagi valesti!",
                     incorrect_msg = "Oled funktsioonile `str` andnud vale väärtusega argumendi")





#
success_msg("Tubli! Pane tähele, et impordil tekkisid väga pikad tunnusenimed. Seega nõuavad imporditavad failid vahel ka eeltööd. Siin oleks eelnevalt tulnud tunnusenimesid kohendada, need peaks olema sisukad, kuid võimalusel mitte väga pikad. Veerupäises olevad tühikud ja erisümbolid teisendatakse punktideks.")

 

```

--- type:NormalExercise lang:r xp:100 skills:3 key:8369286757
## Andmete import 2


Andmete impordiks tekstifailist saab kasutada käsku `read.table()`. 

Funktsiooni `read.table()` argumentide abil saab paika panna, mis on imporditavas failis veergude eraldaja, mis sümbolit kasutatakse kümnendkoha määramisel, kas veergudel on olemas nimed jne.



*** =instructions

- **Ülesanne 1** Kasutades käsku `read.table()` impordi R-i fail *tulemused.txt* aadressilt  *http://kodu.ut.ee/~annes/R/tulemused.txt*, omista andmestik muutujale `andmed2`. Prindi andmestik ekraanile
- **Ülesanne 2** Vaata andmestiku tunnuste ülevaadet käsuga `summary()`.


*** =hint
- Ava fail brauseri aknas ja vaata, mis on veergude eraldaja ja milline sümbol on kümnendkohtade eraldajaks.
- Kaldkriipsu `\` saad eraldajana esitada nii `sep = "\\"`.
- Andmetabelis on 5 vaatlust ja 2 tunnust, üks tekstiline ja üks arvuline.


*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Ülesanne 1: Impordi andmed, moodustades objekti andmed2. Prindi saadud objekt ekraanile
andmed2 <- read.table(_________________________________)



# Ülesanne 2: Vaata andmestiku tunnuste ülevaadet


 

```

*** =solution
```{r}
# Ülesanne 1: Impordi andmed, moodustades objekti andmed2. Prindi saadud objekt ekraanile
andmed2 <- read.table("http://kodu.ut.ee/~annes/R/tulemused.txt", header = T, sep = "\\", dec = ",")
andmed2


# Ülesanne 2: Vaata andmestiku tunnuste ülevaadet
summary(andmed2)



```

*** =sct
```{r}
# 1
#test_function_result(name = "read.table",
#                     index = 1,
#                     eq_condition = "equivalent",
#                     not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `read.table`",
#                     error_msg = "Esimeses ülesandes on midagi valesti!",
#                     incorrect_msg = "Oled funktsioonile `read.table` andnud vale väärtusega argumendi")
 
test_function(name = "read.table",
              args = c("header", "sep", "dec"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `read.table`",
             args_not_specified_msg = paste("Määra `read.table` käsus argumendi", c("`header`", "`sep`", "`dec`"), "väärtus."),
             incorrect_msg = paste("Oled funktsioonis `read.table` andnud vale väärtuse argumendile",  c("`header`", "`sep`", "`dec`"))) 
 

 

#    not_called_msg: in case the student did not call the function
#    args_not_specified_msg: in case the student did not specify all arguments listed in args.
#    incorrect_msg: in the case the student did not correctly specify all arguments listed in args.
 
#test_object("andmed2",  
#            undefined_msg = "Objekt `andmed2` on defineerimata.",
#           incorrect_msg = "Objekti `andmed2` väärtus ei ole korrektne. Proovi uuesti.") 


test_data_frame("andmed2",  
                columns = c("nimi",  "tulemus"),
                eq_condition = "equivalent",
                undefined_msg = "Andmestik `andmed2` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `andmed2`.",
                incorrect_msg = "Objekti `andmed2` väärtus ei ole korrektne. Proovi uuesti.") 

 
 
test_output_contains(expr = "andmed2",
                     times = 1,
                     incorrect_msg = "Andmestik on ekraanile printimata.")
 
 


# 2
test_function_result(name = "summary",
                     index = 1,
                     eq_condition = "equivalent",
                     not_called_msg = "Teises ülesandes pead kasutama funktsiooni `summary`",
                     error_msg = "Teises ülesandes on midagi valesti!",
                     incorrect_msg = "Oled funktsioonis `summary` andnud vale väärtusega argumendi")




#
success_msg("Hästi! Liigu järgmise ülesande juurde.")
```











--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:d7c15a630f
## Andmete import  3

Vaata abiinfot funktsioonile `read.csv`. Selleks kirjuta käsureale:

```{r, prompt = T}
?read.csv

```

Loe avanevast failist funktsiooni argumentide ja töö kirjeldust.

Seejärel vali õige vastusevariant.




*** =instructions
- Funktsiooni `read.csv` argumentide vaikeväärtused määravad, et imporditavas failis peab väljaeraldajaks olema semikoolon.
- Funktsiooni `read.csv` ei saa kasutada *.txt*-laiendiga faili importimiseks.
- Funktsiooni `read.csv` argumentide vaikeväärtused määravad, et imporditavas failis peab kümnendemurru eraldajaks olema punkt.
- Funktsiooni `read.csv` argumentide vaikeväärtused määravad, et imporditavas failis peab kümnendemurru eraldajaks olema koma.

*** =hint
- Funktsiooni argumentide vaikeväärtuste leidmiseks vaata abilehelt **Usage** plokist funktsiooni argumente, kui argumendil on võrdusmärgiga omistatud mingi väärtus, siis see ongi vaikeväärtus, mida funtksioon kasutab, kui kasutaja ei ole määranud teisiti. Näiteks funktsiooni `read.table` korral: `read.table(file, header = FALSE, dec = ".", ...)` saame, et faili nimel pole vaikeväärtust, selle peab kasutaja ise määrama, aga vaikimisi eeldab funktsioon, et veergudel pole päist(`header = FALSE`) ning kümnedekoha eraldajaks on vaikimisi punkt (`dec = "."`). 
 

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg1 = "Vale vastus! Selle funktsiooni korral on veergude eraldaja  `sep` vaikeväärtus koma."
msg2 = "Vale vastus! Ka *txt.*-laiendiga failid saab selle funktsiooniga R-i importida."
msg3 = "Õige vastus! "
msg4 = "Vale vastus! Selle funktsiooni korral on kümnendemurru eraldaja `dec` vaikimisi väärtus punkt."

test_mc(correct = 3, feedback_msgs = c(msg1, msg2, msg3, msg4))
```














--- type:NormalExercise lang:r xp:100 skills:3 key:02d3d1b32a
## Andmete import 4

Funktsioonide `read.csv()` ja `read.csv2()` kasutamine.


Impordi andmed failist *A.csv*.


*** =instructions
- **Ülesanne 1** Loe funktsioonide `read.csv()` ja `read.csv2()` abilehte. Tee kindlaks, mis argumendi abil saab määrata maksimaalse imporditava ridade arvu. Omista selle argumendi nimi stringina muutujale nimega `argumendinimi`.
- **Ülesanne 2**: Kontrolli, kas fail *A.csv*  on juba töökaustas olemas, kasuta selleks käsku `list.files()`. Tulemuseks peab olema faili nimi. Faili saad vaadata ka aadressil *http://kodu.ut.ee/~annes/R/A.csv*  
- **Ülesanne 3**: Impordi failist *A.csv* andmed, kasuta selleks funktsiooni `read.csv()` või `read.csv2()`, vali see funktsioon, mille korral pead vähem argumente väärtustama st see, mis argumentide vaikeväärtuste poolest paremini sobib.  Omista andmestik muutujale `andmed4`.  Pane tähele, et failis on andmeteploki all kommentaaritekst, mille peab importimisel välja jätma.
- **Ülesanne 4**: Omista muutujale `valik` andmestikust `andmed4` esimesed 10 rida ja kõik veerud väljaarvatud neljas ja viies. Prindi ekraanile. 


*** =hint
- Kasuta toodud faili impordiks funktsiooni `read.csv2`
- Andmestikust alamosa valikuks kasuta kandilisi sulge ja viitamist rea/veeru indeksitega. Negatiivne indeks jätab vastava elemendi valikust välja.




*** =pre_exercise_code
```{r}

download.file("http://kodu.ut.ee/~annes/R/A.csv", "A.csv",  mode = "wb")

```

*** =sample_code
```{r}
# Ülesanne 1: Omista muutujale selle argumendi nimi, mis määrab imporditava ridade arvu
argumendinimi <- "_______________"


# Ülesanne 2: kontrolli faili olemasolu töökaustas
 


# Ülesanne 3: täienda antud koodi
andmed4 <- read.csv__("A.csv", ____________)


# Ülesanne 4: prindi ekraanile nõutud alamosa andmestikust
valik <- ______________
valik


```

*** =solution
```{r}
# Ülesanne 1: Omista muutujale selle argumendi nimi, mis määrab imporditava ridade arvu
argumendinimi <- "nrows"


# Ülesanne 2: kontrolli faili olemasolu töökaustas
list.files() 


# Ülesanne 3: täienda antud koodi
andmed4 <- read.csv2("A.csv", nrows = 45)


# Ülesanne 4: prindi ekraanile nõutud alamosa andmestikust
valik <- andmed4[1:10, -(4:5)]
valik

```

*** =sct
```{r}
# 1
test_object("argumendinimi",  
            undefined_msg = "Objekt `argumendinimi` on defineerimata.",
            incorrect_msg = "Objekti `argumendinimi` väärtus ei ole korrektne. Proovi uuesti.") 
 
# 2
test_function(name = "list.files",
              args = NULL,
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Teises ülesandes pead kasutama funktsiooni `list.files`",
             args_not_specified_msg = NULL,
             incorrect_msg = "Funktsiooni `list.files` korral pole praegu argumente vaja määrata") 
 


# 3
test_function(name = "read.csv2",
              args = c("file", "nrows"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Kolmandas ülesandes pead kasutama funktsiooni `read.csv2`",
             args_not_specified_msg = paste("Määra `read.csv2` käsus argumendi", c("`file`", "`nrows`"), "väärtus."),
             incorrect_msg = paste("Oled funktsioonis `read.csv2` andnud vale väärtuse argumendile",  c("`file`", "`nrows`"))) 
 #    not_called_msg: in case the student did not call the function
#    args_not_specified_msg: in case the student did not specify all arguments listed in args.
#    incorrect_msg: in the case the student did not correctly specify all arguments listed in args.
 
 
 
#test_object("andmed4",  
#            undefined_msg = "Objekt `andmed4` on defineerimata.",
#            incorrect_msg = "Objekti `andmed4` väärtus ei ole korrektne. Proovi uuesti.") 


test_data_frame("andmed4",  
                columns = c( "id",   "sugu",   "vanus",   "elukoht",   "visiit",   "kasv",   "kaal",   "sirutus"),
                eq_condition = "equal",
                undefined_msg = "Andmestik `andmed4` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `andmed4`.",
                incorrect_msg = "Objekti `andmed4` väärtus ei ole korrektne. Proovi uuesti.") 

 

 
#4 
#test_object("valik",  
#            undefined_msg = "Objekt `valik` on defineerimata.",
#            incorrect_msg = "Objekti `valik` väärtus ei ole korrektne. Proovi uuesti.") 
test_data_frame("valik",  
                columns = c( "id",   "sugu",   "vanus",    "kasv",   "kaal",   "sirutus"),
                eq_condition = "equal",
                undefined_msg = "Andmestik `valik` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `valik`.",
                incorrect_msg = "Objekti `valik` väärtus ei ole korrektne. Proovi uuesti.") 

 



test_output_contains(expr = "valik",
                     times = 1,
                     incorrect_msg = "Valitud osa andmetest on ekraanile printimata.")



 
#
success_msg("Hästi! Liigu järgmise ülesande juurde.")



```




--- type:NormalExercise lang:r xp:100 skills:3 key:b555eb5148
## Andmete import 5

Töölaual on andmestiku fail nimega *B.csv*, failis on andmed 160 isiku testitulemustega. Fail on R-i imporditud järgmise käsu abil:

```{r, prompt = T}
andmed5a <- read.csv2("B.csv")

```

Kui andmestiku objekti uurida, siis ilmneb, et midagi on impordil läinud valesti. Ülesandes peadki leidma vea ja tegema importimise käsku parandused.




*** =instructions
- **Ülesanne 1**: Vaata, mis on imporditud andmestiku `andmed5a` dimensioon (`dim`), millised on tunnused (`str`). Prindi ekraanile andmestiku esimese 5 veeru lõpp käsuga `tail`.
- **Ülesanne 2**: Täienda antud koodi nii, et andmete impordi tulemus oleks korrektne (korrektne arv vaatlusi). Lisaks kasuta funktsiooni `read.csv2` argumenti, mis määraks tekstiliste tunnuste tüübiks `character` mitte `Factor`. Omista tekkiv andmestik muutujale `andmed5`. 
- **Ülesanne 3**: Moodusta andmestik `valik`, kus oleks andmestiku `andmed5` kõik vaatlused, kuid veergudest vaid need, mille nimi algab sõnega *hinnang* või *taust*. 

*** =hint
- Pane tähele, et näites imporditud andmestikuobjektis on lisaks andmetele ka failis olnud kommentaarid sisse loetud.
- Tekstitunnuste importimisel faktorite tekitamise keelamiseks kasuta argumenti `stringsAsFactors`.
- Viimases ülesandes saad kasutada funktsiooni `substr`. Vaata ka sarnase ülesande näidet teise praktikumi juhendist.


*** =pre_exercise_code
```{r}
download.file("http://kodu.ut.ee/~annes/R/B.csv", "B.csv",  mode = "wb")
andmed5a <- read.csv2("B.csv")

```




*** =sample_code
```{r}
# Ülesanne 1: Pane kirja sobivad funktsiooninimed, ning viimases käsus sobivad indeksid
_____(andmed5a)
_____(andmed5a)
tail(andmed5a[ , ___:___ ])


# Ülesanne 2: tee antud koodi vajalik täiendus, prindi tulemus ekraanile
andmed5 <-  read.csv2(file = "B.csv", ________________)


# Ülesanne 3: vali andmestikust nõutud alamosa
valik <- __________________________


```





*** =solution
```{r}
# Ülesanne 1: Pane kirja sobivad funktsiooninimed, ning viimases käsus sobivad indeksid
dim(andmed5a)
str(andmed5a)
tail(andmed5a[ , 1:5 ])


# Ülesanne 2: tee antud koodi vajalik täiendus, prindi tulemus ekraanile
andmed5 <-  read.csv2(file = "B.csv",   nrows = 160, stringsAsFactors = FALSE)


# Ülesanne 3: vali andmestikust nõutud alamosa
valik <- andmed5[, substr(names(andmed5), 1, 5) %in% c("taust", "hinna")]
valik
```

*** =sct
```{r}

test_predefined_objects("andmed5a", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `andmed5a`.", 
                        incorrect_msg = "Ära muuda objekti `andmed5a` väärtust.")
 

# 1
test_function(name = "dim",
              args = c("x"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead kõigepealt kasutama funktsiooni `dim`",
             args_not_specified_msg = paste("Määra `dim` käsus argumendiks andmestik `andmed5a`."),
             incorrect_msg = paste("Pane funktsioonile `dim` argumendiks andmestik `andmed5a`.")) 
 

test_function(name = "str",
              args = c("object"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead teiseks kasutama funktsiooni `names`",
             args_not_specified_msg = paste("Määra `str` käsus argumendiks andmestik `andmed5a`."),
             incorrect_msg = paste("Pane funktsioonile `str` argumendiks andmestik `andmed5a`.")) 
 

test_function(name = "tail",
              args = c("x"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead viimaseks kasutama funktsiooni `tail`",
             args_not_specified_msg = paste("Määra `tail` käsus argumendiks andmestiku `andmed5a` viis esimest veeru."),
             incorrect_msg = paste("Pane funktsioonile `tail` argumendiks andmestiku `andmed5a` viis esimest veeru.")) 
 


# 2
test_function(name = "read.csv2",
              args = c("file", "nrows", "stringsAsFactors"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Teises ülesandes pead kasutama funktsiooni `read.csv2`",
             args_not_specified_msg = paste("Määra `read.csv2` käsus argumendi", c("`file`", "`nrows`", "`stringsAsFactors`"), "väärtus."),
             incorrect_msg = paste("Oled funktsioonis `read.csv2` andnud vale väärtuse argumendile",  c("`file`", "`nrows`", "`stringsAsFactors`"))) 
 #    not_called_msg: in case the student did not call the function
#    args_not_specified_msg: in case the student did not specify all arguments listed in args.
#    incorrect_msg: in the case the student did not correctly specify all arguments listed in args.
 
#test_object("andmed5",  
#            undefined_msg = "Objekt `andmed5` on defineerimata.",
#            incorrect_msg = "Objekti `andmed5` väärtus ei ole korrektne. Proovi uuesti.") 
 

test_data_frame("andmed5",  
                columns = NULL,
                eq_condition = "equal",
                undefined_msg = "Andmestik `andmed5` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `andmed5`.",
                incorrect_msg = "Objekti `andmed5` väärtus ei ole korrektne. Proovi uuesti.") 

 
 

 


# 3
#test_object("valik",  
#            undefined_msg = "Objekt `valik` on defineerimata.",
#            incorrect_msg = "Objekti `valik` väärtus ei ole korrektne. Proovi nõutud veergude valik uuesti teha.") 
test_data_frame("valik",  
                columns = NULL,
                eq_condition = "equal",
                undefined_msg = "Andmestik `valik` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `valik`.",
                incorrect_msg = "Objekti `valik` väärtus ei ole korrektne. Proovi uuesti.") 

   


#
success_msg("Tubli!")




```




