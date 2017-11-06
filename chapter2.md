---
title       : Toimingud andmestikuga
description : Insert the chapter description here
--- type:NormalExercise lang:r xp:100 skills:3 key:e952bf341c
## Andmete filtreerimine 1

Kasutame andmestikku `pojad`. Mõõdetud on perede esimese ja teise poja pea pikkus ja laius. Mõõtmised on millimeetrites. Tunnused andmestikus on järgmised:

- `l1` – esimese poja pea pikkus
- `l2` – teise poja pea pikkus
- `b1` – esimese poja pea laius
- `b2` – teise poja pea laius



*** =instructions
- **Ülesanne 1** Töölaual on olemas andmestik  `pojad`. Prindi see ekraanile.
- **Ülesanne 2** Moodusta tõeväärtusvektor nimega `filter`, mille väärtus on `TRUE` kui pere esimese poja pea pikkus on keskmisest suurem. Prindi loodud filter ekraanile.
- **Ülesanne 3** Vali andmestikust alamosa: need pered, kus esimese poja pea pikkus on keskmisest suurem, kasutades eelnevalt loodud filtritunnust. Omista valitud read andmestikust objektile `pojad1`. Rakenda loodud andmestikule funktsiooni `dim()`.


*** =hint
- Keskmise pea pikkuse esimese poja korral saad leida käsuga `mean(pojad$l1)`. Võrdluse kirjapanekuks kasuta märke `>` või `<`.
- Andmete filtreerimiseks kasuta kas `subset` funktsiooni või kantsulge: `pojad[filter,]`.  Objektide valimiseks andmestikust tuleb filtritunnuse nimi kirjutada kantsulgusesse esimesele kohale st enne koma.

*** =pre_exercise_code
```{r}
pojad <- read.table("http://math.ut.ee/~annes/R/pojad.txt", header = T)


```

*** =sample_code
```{r}
# Ülesanne 1: prindi andmestik ekraanile


# Ülesanne 2: moodusta tõeväärtusvektor
filter <- ___________________________
filter


# Ülesanne 3: vali tingimusele vastavad read andmestikust, küsi andmestiku dimensioone
pojad1 <- ____________________
______(pojad1)


```

*** =solution
```{r}
# Ülesanne 1: prindi andmestik ekraanile
pojad

# Ülesanne 2: moodusta tõeväärtusvektor
filter <- pojad$l1 > mean(pojad$l1)
filter


# Ülesanne 3: vali tingimusele vastavad read andmestikust, küsi andmestiku dimensioone
pojad1 <- pojad[filter, ]
dim(pojad1)



```

*** =sct
```{r}

test_predefined_objects("pojad", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Oled andmestiku `pojad` ära kustutanud, alusta uuesti", 
                        incorrect_msg = "Oled andmestiku `pojad` sisu muutnud. Alusta uuesti.")


# 1
test_output_contains(expr = "pojad",
                     times = 1,
                     incorrect_msg = "ÜL1: andmestik on ekraanile printimata.")


# 2
test_object("filter",  
            undefined_msg = "Tõeväärtuste vektor `filter` on defineerimata.",
            incorrect_msg = "Tõeväärtuste vektori `filter` väärtus ei ole korrektne. Proovi uuesti.") 

test_output_contains(expr = "filter",
                     times = 1,
                     incorrect_msg = "ÜL2: filteritunnus on ekraanile printimata.")

#3
#test_object("pojad1",  
#            undefined_msg = "Andmetabel  `pojad1` on defineerimata.",
#            incorrect_msg = "Andmetabeli `pojad1` väärtus ei ole korrektne. Proovi uuesti.") 
            
 

test_data_frame("pojad1",  
                columns = c("l1", "b1", "l2", "b2"),
                eq_condition = "equal",
                undefined_msg = "Andmestik `pojad1` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `pojad1`.",
                incorrect_msg = "Andmestik `pojad1` ei vasta tingimustele. Proovi uuesti.") 

 
  
            
test_function(name = "dim",
              args = "x",
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Viimases ülesandes pead kasutama funktsiooni `dim`.",
             args_not_specified_msg = "Määra `dim` käsu argumendiks andmestik `pojad1`.",
             incorrect_msg = "Oled funktsioonile `dim` andnud vale argumendi.") 



#
success_msg("Tubli!")


```

--- type:NormalExercise lang:r xp:100 skills:3 key:6ebe6ecdf4
## Andmete filtreerimine 2

Kasutame admestikku `kapsad`. Uuritud on kahe kapsasordi kapsapeade kaalu ja vitamiinide sisaldust.  Tunnused andmestikus on järgmised:

- `Cult` -    kapsa sort 
- `Date` - külvikuupäev: 16., 20. või 21. kuupäev
- `HeadWt` - kapsapea kaal, kg
- `VitC` - kapsapea C-vitamiini sisaldus




*** =instructions
- **Ülesanne 1** Töölaual on olemas andmestik  `kapsad`. Prindi selle andmestiku kirjeldus käsuga `summary()` ekraanile.
- **Ülesanne 2** Moodusta kaks tõeväärtusvektorit. Esimene nimega `filter1`, mille väärtus on `TRUE`, kui kapsapea on sordist `c52` ja `FALSE` vastasel juhul. Teine vektor nimega `filter2`, mille väärtus on `TRUE`, kui kapsas on külvatud 21. kuupäeval (`d21`) ja `FALSE` vastasel juhul. 
- **Ülesanne 3** Kasutades loodud filtreid ja sobivat loogilist tehet vali andmestikust alamosa: need kapsad, mis on sordist `c52` ning on külvatud 21. kuupäeval. Omista valitud read andmestikust objektile `kapsad1`. 
- **Ülesanne 4** Kasutades loodud filtreid ja sobivat loogilist tehet vali andmestikust alamosa: need kapsad, mis on sordist `c52` või on külvatud 21. kuupäeval. Omista valitud read andmestikust objektile `kapsad2`. 
- **Ülesanne 5** Kummas alamandmestikus on rohkem vaatlusi? Omista selle andmestiku nimi stringina muutujale  `kumbsuurem`.


 

*** =hint
- Loogilise võrdumise kontrolliks kasuta topelt võrdusmärki `==`.
- Andmete filtreerimiseks kasuta kas `subset` funktsiooni või kantsulge: `kapsad[________,  ]`. Objektide valimiseks andmestikust tuleb filteritunnuse nimi kirjutada kantsulgusesse esimesele kohale st enne koma.
 



*** =pre_exercise_code
```{r}
kapsad <- read.table("http://math.ut.ee/~annes/R/cabbages.txt", header = T)


```

*** =sample_code
```{r}
# Ülesanne 1: prindi andmestiku kirjeldus nõutud käsuga


# Ülesanne 2: moodusta tõeväärtusvektorid
filter1 <- ___________________________
filter2 <- ___________________________


# Ülesanne 3: vali tingimusele vastavad read andmestikust 
kapsad1 <- ____________________
 

# Ülesanne 4:  vali tingimusele vastavad read andmestikust 
kapsad2 <- ____________________


# Ülesanne 5:  pane kirja suurema objektide arvuga andmetabeli nimi
kumbsuurem <- "__________________"



```

*** =solution
```{r}
# Ülesanne 1: prindi andmestiku kirjeldus nõutud käsuga
summary(kapsad)

# Ülesanne 2: moodusta tõeväärtusvektorid
filter1 <- kapsad$Cult == "c52"
filter2 <- kapsad$Date == "d21"


# Ülesanne 3: vali tingimusele vastavad read andmestikust 
kapsad1 <- kapsad[filter1 & filter2, ]
 

# Ülesanne 4:  vali tingimusele vastavad read andmestikust 
kapsad2 <- kapsad[filter1 | filter2, ]


# Ülesanne 5: pane kirja suurema objektide arvuga andmetabeli nimi
kumbsuurem <- "kapsad2"


```

*** =sct
```{r}

test_predefined_objects("kapsad", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Oled andmestiku `kapsad` ära kustutanud, alusta uuesti", 
                        incorrect_msg = "Oled andmestiku `kapsad` sisu muutnud. Alusta uuesti.")


# 1
test_function(name = "summary",
              args = "object",
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `summary`.",
             args_not_specified_msg = paste("Määra `summary` käsu argumendiks andmestik `kapsad`."),
             incorrect_msg = paste("Oled funktsioonile `summary` andnud ette vale andmestiku.")) 


# 2
test_object("filter1",  
            undefined_msg = "Tõeväärtuste vektor `filter1` on defineerimata.",
            incorrect_msg = "Tõeväärtuste vektori `filter1` väärtus ei ole korrektne. Proovi uuesti.") 
test_object("filter2",  
            undefined_msg = "Tõeväärtuste vektor `filter2` on defineerimata.",
            incorrect_msg = "Tõeväärtuste vektori `filter2` väärtus ei ole korrektne. Proovi uuesti.") 

 
#3
#test_object("kapsad1",  
#            undefined_msg = "Andmetabel  `kapsad1` on defineerimata.",
#            incorrect_msg = "Andmetabeli `kapsad1` väärtus ei ole korrektne. Proovi alamosa valik uuesti teha. Tingimuse kirjapanekul pead loogilise tehtena kasutama korrutamist `&`.") 
            
#4
#test_object("kapsad2",  
#            undefined_msg = "Andmetabel  `kapsad2` on defineerimata.",
#            incorrect_msg = "Andmetabeli `kapsad2` väärtus ei ole korrektne. Proovi alamosa valik uuesti teha. Tingimuse kirjapanekul pead loogilise tehtena kasutama liitmist `|`") 
            
 
#3
test_data_frame("kapsad1",  
                columns = c("Cult",   "Date" ,  "HeadWt", "VitC" ),
                eq_condition = "equal",
                undefined_msg = "Andmestik `kapsad1` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `kapsad1`.",
                incorrect_msg = "Andmestik `kapsad1` ei vasta tingimustele. Proovi uuesti.") 
#4
test_data_frame("kapsad2",  
                columns = c("Cult",   "Date" ,  "HeadWt", "VitC" ),
                eq_condition = "equal",
                undefined_msg = "Andmestik `kapsad2` on defineerimata.",
                undefined_cols_msg = "Kontrolli, mis tunnused on andmestikus `kapsad2`.",
                incorrect_msg = "Andmestik `kapsad2` ei vasta tingimustele. Proovi uuesti.") 

    
 
 
 
 
                        
#5            
test_object("kumbsuurem",  
            undefined_msg = "Viimase ülesande muutuja `kumbsuurem` on defineerimata.",
            incorrect_msg = "Viimase ülesande muutuja `kumbsuurem` väärtus ei ole korrektne. Proovi uuesti.") 


#
success_msg("Super! Jätka samas vaimus.")
```

--- type:NormalExercise lang:r xp:100 skills:3 key:d74da93dea
## Tunnuste lisamine andmestikku

Analüüsi käigus on sageli vaja olemasolevaid tunnuseid teisendada või arvutada uusi tunnuseid. Andmetabelisse tunnuste lisamisel lisatakse uued veerud andmetabeli lõppu.


Kasutame andmestikku `pojad`. Mõõdetud on perede esimese ja teise poja pea pikkus ja laius. Mõõtmised on millimeetrites. Tunnused andmestikus on järgmised:

- `l1` – esimese poja pea pikkus
- `l2` – teise poja pea pikkus
- `b1` – esimese poja pea laius
- `b2` – teise poja pea laius




*** =instructions
- **Ülesanne 1** Lisa olemasolevasse andmestikku tunnus `pikkus_vahe`, mille väärtuseks on esimese ja teise poja pea pikkuse vahe (esimene - teine).  
- **Ülesanne 2** Lisa olemasolevasse andmestikku tunnus `laus_suhe`, mille väärtuseks on esimese ja teise poja pea laiuse suhe (esimene / teine).  
- **Ülesanne 3** Moodusta andmestikuobjekt `uus`, kus oleks samad objektid ja samad 6 tunnust kui andmestikus `pojad`, kuid erinev oleks tunnuste järjestus andmestikus.  Andestiku `uus` tunnused peaks olema järjestuses:  `l1`, `l2`, `pikkus_vahe`, `b1`, `b2`, `laius_suhe`.

*** =hint
- Tunnuse lisamiseks andmestikku saab kasutada omistamist kujul `andmed$uusveerg <- väärtused` või `andmed[, "uusveerg"] <- väärtused`.
- veergude ümberjärjestamiseks pead kantsulgudesse teisele kohale panema uut järjestust näitava indeksite vektori või uues järjestuses veerupäiste nimedaga vektori.

*** =pre_exercise_code
```{r}
pojad <- read.table("http://math.ut.ee/~annes/R/pojad.txt", header = T)

```

*** =sample_code
```{r}
# Vaata meeldetuletuseks andmestikku:
summary(pojad)

# Ülesanne 1: uue tunnuse lisamine, vahe


# Ülesanne 2: uue tunnuse lisamine, suhe


# Ülesanne 3: andmestiku veergude ümberjärjestamine
uus <- pojad[, ____________]

 


```

*** =solution
```{r}
# Vaata meeldetuletuseks andmestikku:
summary(pojad)

# Ülesanne 1: uue tunnuse lisamine, vahe
pojad$pikkus_vahe <- pojad$l1 - pojad$l2


# Ülesanne 2: uue tunnuse lisamine, suhe
pojad$laius_suhe <- pojad$b1 / pojad$b2


# Ülesanne 3: andmestiku veergude ümberjärjestamine
uus <- pojad[, c("l1", "l2", "pikkus_vahe", "b1", "b2", "laius_suhe")]

 

```

*** =sct
```{r}

#test_predefined_objects("pojad", 
#                        eq_condition = "equivalent",
#                        eval = TRUE,
#                        undefined_msg = "Oled andmestiku `pojad` ära kustutanud, alusta uuesti", 
#                        incorrect_msg = "Oled andmestiku `pojad` sisu muutnud. Alusta uuesti.")




# 1
test_data_frame("pojad", columns = c("pikkus_vahe"),
                eq_condition = "equal",
                undefined_msg = "Ära kustuta andmstikku `pojad`!",
                undefined_cols_msg = "Kas oled andmestikku `pojad` lisanud veeru `pikkus_vahe`?",
                incorrect_msg = "Kas oled uue tunnuse `pikkus_vahe` õigesti arvutanud ja omistanud: `pojad$pikkus_vahe <- pojad$l1 - pojad$l2`?")


# 2
test_data_frame("pojad", columns = c("laius_suhe"),
                eq_condition = "equal",
                undefined_msg = "Ära kustuta andmstikku `pojad`!",
                undefined_cols_msg = "Kas oled andmestikku `pojad` lisanud veeru `laius_suhe`?",
                incorrect_msg = "Kas oled uue tunnuse `laus_suhe` õigesti arvutanud ja omistanud: `pojad$laus_suhe <- pojad$b1 / pojad$b2`?")

#3
#test_object("uus",  
#            undefined_msg = "Andmetabel  `uus` on defineerimata.",
#            incorrect_msg = "Andmetabeli `uus` sisu ei ole korrektne. Proovi uuesti.") 
            
          
test_data_frame("uus", 
            eq_condition = "equal",
            columns = c("l1", "l2", "pikkus_vahe", "b1", "b2", "laius_suhe"),
                undefined_msg = "Kas moodustasid uue andmestiku `uus`?",
                undefined_cols_msg = "Kas oled andmestikku `uus` valinud kõik nõutud veerud?",
                incorrect_msg = "Kas oled andmestiku `uus` veerud määranud nii nagu vaja?")

  


#
success_msg("Tubli!")







```

--- type:NormalExercise lang:r xp:100 skills:3 key:085db7f347
## Paranda viga andmestikus

Enne analüüsiga alustamist on alati vaja andmeid ka kontrollida ja võimalusel leitud vead parandada. 


Töölaual on andmestik `dieet`. Tegu on teatavate dieetide mõju uuringuga. Uuringus osalejaid on kaalutud enne dieeti (`kaal1`) ja pärast dieeti (`kaal2`). Lisaks on teada iga inimese identifikaator ja dieedi tüüp.
 


*** =instructions
- **Ülesanne 1** Töölaual on olemas andmestik  `dieet`. Prindi selle andmestiku kirjeldus käsuga `summary()` ekraanile.
- **Ülesanne 2** Teada on, et ühel objektil on kaalu väärtus kilogrammide asemel sisestatud grammides. Leia see vaatlus ja tee parandus.
- **Ülesanne 3** Lisaks on ühel vaatlusel teise  kaalumise väärtuse sisestamisel tekkinud viga: kaalu väärtus 350 ei ole korrektne. Kuna õiget kaalu väärtust pole enam võimalik tagantjärele saada, siis asenda vigane väärtus tühikuga. 



*** =hint
- `summary` käsust näed, et grammides kaal esineb esimese kaalutunnuse korral.
- Et leida, millisel objektil on kaal sisestatud grammides ehk millisel objektil on `kaal1` maksimaalne, saad kasutada funktsiooni `which.max()`.
- Andmestikus oleva väärtuse muutmiseks pead tegema omistamistehte, näiteks  kujul `andmed[veagaobjektiindeks, tunnusenr] <- õigeväärtus`.
- Tühiku lisamiseks andmestikku kasuta funktsiooni `is.na()` abi.


*** =pre_exercise_code
```{r}
set.seed(123)
n <- 365
id <- sample(100:999, size = n)
grupp <- sample(letters[1:5], size = n, replace= T)
kaal1 <- round(rnorm(n, m = 80, s = 15))
kaal2 <- round(kaal1 * 1.2 + rnorm(n, s = 10)  + as.numeric(as.factor(grupp))*rbinom(n, 1,   .5))
dieet <- data.frame(id, grupp, kaal1, kaal2)
dieet[250, "kaal1"] <- dieet[25, "kaal1"]*1000
dieet[145, "kaal2"] <- 350
 
rm(n, id, grupp, kaal1, kaal2)

```

*** =sample_code
```{r}
# Ülesanne 1: prindi andmestiku kirjeldus nõutud käsuga



# Ülesanne 2: Tee grammides kaalule teisendus kilodeks



# Ülesanne 3: Asenda vigane väärtus tühikuga



```



*** =solution
```{r}
# Ülesanne 1: prindi andmestiku kirjeldus nõutud käsuga
summary(dieet)


# Ülesanne 2: Tee grammides kaalule teisendus kilodeks
dieet[which.max(dieet$kaal1), "kaal1"] <- dieet[which.max(dieet$kaal1), "kaal1"] /1000


# Ülesanne 3: Asenda vigane väärtus tühikuga
is.na(dieet[which.max(dieet$kaal2), "kaal2"]) <- TRUE


```

*** =sct
```{r}

# 1
#test_function(name = "summary",
#              args = "object",
#              index = 1,
#             eq_condition = "equivalent",
#             not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `summary`.",
#             args_not_specified_msg = paste("Määra `summary` käsu argumendiks andmestik `dieet`."),
#             incorrect_msg = paste("Oled funktsioonile `summary` andnud ette vale andmestiku.")) 

test_student_typed("summary(dieet)", not_typed_msg =  "Kas kasutasid `summary` funktsiooni?")



#2
test_data_frame("dieet", columns = c("kaal1"),
                undefined_msg = "Ära kustuta andmestikku `dieet`!",
                undefined_cols_msg = "Oled andmestikust tunnuse `kaal1` kustutanud. Alusta uuesti.",
                incorrect_msg = "Veerus `kaal1` ei ole õiged väärtused. Oled ülesande 2 teisenduses vea teinud.")

#3
test_data_frame("dieet", columns = c("kaal2"),
                undefined_msg = "Ära kustuta andmestikku `dieet`!",
                undefined_cols_msg = "Oled andmestikust tunnuse `kaal2` kustutanud. Alusta uuesti.",
                incorrect_msg = "Veerus `kaal2` ei ole õiged väärtused. Tühiku omistamiseks kasuta käsku `is.na(dieet[dieet$kaal2 == 350, 'kaal2']) <- TRUE`")



#
success_msg("Tubli!")



```







--- type:NormalExercise lang:r xp:100 skills:3 key:5085e10f46
## Hulgatehted

Hulgatehtedeid saab R-is teha  järgmiste käskudega

- ühend `union`
- ühisosa `intersect`
- vahe `setdiff`


Töölaual on olemas kaks andmestikku: 

- andmestikus `A` on kirjas vastajate id-kood, sugu, elukoht, vanus, pikkus, kaal, käte siruulatus ning arstivisiidi toimumine
- andmestikus `B` on kirjas vastajate id-kood, uuringugrupi tunnus ning vastused mitmesugustele testidele



Uurida tuleb vaatlusobjektide kattuvust. Loe tähelepanelikult ülesannete teksti!


*** =instructions

- **Ülesanne 1** Kontrolli id-koodi põhjal ja sobivat hulgatehet kasutades, millised isikud esinevad andmestikus `B`, kuid mitte andmestikus `A`. Omista nende isikute id-koodidide  vektor muutujale `olemasBmitteA`.
- **Ülesanne 2** Kontrolli id-koodi põhjal, millised isikud esinevad mõlemas andmestikus. Omista nende isikute id-koodide tähestiku järgi kahanevalt järjestatud vektor muutujale `AjaB`.


*** =hint
- vektori sorteerimiseks kasuta käsku `sort`, kaheneva järjestuse määramiseks muuda argumendi `decreasing` väärtust.



*** =pre_exercise_code
```{r}
A <- read.csv2("http://kodu.ut.ee/~annes/R/A.csv", nrows = 45)
B <- read.csv2("http://kodu.ut.ee/~annes/R/B.csv", nrows = 160)
B <- B[, c("id", "grupp", sort(names(B)[-(1:2)]))]

```

*** =sample_code
```{r}
# Ülesanne 1: leia isikud, kes on andmestikus B, kuid mitte A-s
olemasBmitteA <- ________________


# Ülesanne 2: leia isikud, kes on mõlemas andmestikus
AjaB <- ________________

```


*** =solution
```{r}
# Ülesanne 1: leia isikud, kes on andmestikus B, kuid mitte A-s
olemasBmitteA <- setdiff(B$id, A$id)


# Ülesanne 2: leia isikud, kes on mõlemas andmestikus
AjaB <- sort(intersect(B$id, A$id), decreasing = TRUE)


```

*** =sct
```{r}


test_predefined_objects("A", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `A`.", 
                        incorrect_msg = "Ära muuda andmestiku `A` sisu.")
 

test_predefined_objects("B", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `B`.", 
                        incorrect_msg = "Ära muuda andmestiku `B` sisu.")



# 1
test_function(name = "setdiff",
              args = c("x", "y"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Esimeses ülesandes pead kasutama funktsiooni `setdiff`",
             args_not_specified_msg = paste("Määra `setdiff` käsus ka kaks argumenti."),
             incorrect_msg = c("Oled funktsioonis `setdiff` andnud vale väärtuse esimesele argumendile, esimesel kohal peab olema andmestiku `B` id-koodi tunnus", 
                                 "Oled funktsioonis `setdiff` andnud vale väärtuse teisele argumendile, teisel kohal peab olema andmestiku `A` id-koodi tunnus")) 

#test_function(name = "sort",
#              args = c("x", "decreasing"),
#              index =2,
#             eq_condition = "equivalent",
#             not_called_msg = "Mõlemas ülesandes pead kasutama ka funktsiooni `sort`",
#             args_not_specified_msg = paste("Määra `sort` käsus", c("esimeseks argumendiks hulgatehte tulemus", "teiseks lisa `decreasing` argument") ),
#             incorrect_msg = paste("Määra `sort` käsus", c("esimeseks argumendiks hulgatehte tulemus", "teiseks argumendiks `decreasing = TRUE`") ))





test_object("olemasBmitteA",  
            undefined_msg = "Muutuja  `olemasBmitteA` on defineerimata.",
            incorrect_msg = "Muutuja `olemasBmitteA` väärtus ei ole korrektne. Proovi uuesti.") 
            
            


#2
test_function(name = "intersect",
              args = NULL,
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Teises ülesandes pead kasutama funktsiooni `intersect`",
             args_not_specified_msg = paste("Määra `intersect` käsus ka kaks argumenti."),
             incorrect_msg = "Oled funktsioonile `intersect` andnud valed argumendid, argumentideks peavad olema id-koodi tunnused mõlemast andmestikust")

test_function(name = "sort",
              args = "decreasing",
              index =1,
             eq_condition = "equivalent",
             not_called_msg = "Teises ülesandes pead kasutama ka funktsiooni `sort`",
             args_not_specified_msg = paste("Määra `sort` käsus  `decreasing` argument."),
             incorrect_msg = paste("Määra `sort` käsus `decreasing = TRUE`") )




test_object("AjaB",  
            undefined_msg = "Muutuja  `AjaB` on defineerimata.",
            incorrect_msg = "Muutuja `AjaB` väärtus ei ole korrektne. Proovi uuesti.") 
            
            






success_msg("Hästi! Liigu järgmise ülesande juurde.")





```

--- type:NormalExercise lang:r xp:100 skills:3 key:152e584365
## Andmestike ühendamine 1

Andmestike ühendamiseks nn võtmetunnuse kaudu saab kasutada käsku `merge`. 


Töölaual on olemas kaks andmestikku: 

- andmestikus `A` on kirjas vastajate id-kood, sugu, elukoht, vanus, pikkus, kaal, käte siruulatus ning arstivisiidi toimumine
- andmestikus `B` on kirjas vastajate id-kood, uuringugrupi tunnus ning vastused mitmesugustele testidele


*** =instructions

- **Ülesanne 1** Liida andmestikud id-koodi tunnuse põhjal, nimeta ühendatud andmestik nimega `uuring1`. Tulemuseks olevas andmestikus peaks olema mõlemast andmestikust kõik isikud.
- **Ülesanne 2** Leia ühendatud andmestiku põhjal tunnuse `test101` keskväärtus ja standardhälve, omista need muuutjatele `kesk` ja `stand`.




*** =hint
- Seda, millised objektid ühendatud andmestikku lähevad, reguleerivad käsu `merge()` argumendid `all, all.x, all.y`.
- Keskväärtuse leidmiseks kasuta käsku `mean()`, standardhälbe jaoks `sd()`.

*** =pre_exercise_code
```{r}
A <- read.csv2("http://kodu.ut.ee/~annes/R/A.csv", nrows = 45)
B <- read.csv2("http://kodu.ut.ee/~annes/R/B.csv", nrows = 160)
B <- B[, c("id", "grupp", sort(names(B)[-(1:2)]))]


```

*** =sample_code
```{r}
# Ülesanne 1: Liida anmdestikud, tulemuses olgu kõik isikud mõlemast andmestikust.
uuring1 <- merge(_____________________)


# Ülesanne 2: leia nõutud keskväärtus ...
kesk <- ________________
# ... ja standardhälve
stand <- ______________



```

*** =solution
```{r}
# Ülesanne 1: Liida anmdestikud, tulemuses olgu kõik isikud mõlemast andmestikust.
uuring1 <- merge(A, B, by = "id", all = TRUE)


# Ülesanne 2: leia nõutud keskväärtus ...
kesk <- mean(uuring1$test101, na.rm = T)
# ... ja standardhälve
stand <- sd(uuring1$test101, na.rm = T)


```



*** =sct
```{r}
test_predefined_objects("A", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `A`.", 
                        incorrect_msg = "Ära muuda andmestiku `A` sisu.")
 

test_predefined_objects("B", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `B`.", 
                        incorrect_msg = "Ära muuda andmestiku `B` sisu.")



# 1
test_function(name = "merge",
              args = c("x", "y", "all"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead  ülesandes  kasutama funktsiooni `merge`",
             args_not_specified_msg = paste("Määra `merge` käsus argumendi", c("`x`", "`y`", "`all`"), "väärtus."),
             incorrect_msg = paste("Muuda `mean` käsus argumendi", c("`x`", "`y`", "`all`"), "väärtust, see pole praegu korrektne.")) 



#test_object("uuring1",  
#            undefined_msg = "Andmestik  `uuring1` on defineerimata.",
#            incorrect_msg = "Andmestiku `uuring1` sisu ei ole korrektne. Proovi uuesti.") 



test_data_frame("uuring1",
                columns = NULL,
                eq_condition = "equivalent",
                undefined_msg = "Andmestik  `uuring1` on defineerimata.",
                incorrect_msg = "Andmestiku `uuring1` sisu ei ole korrektne. Proovi uuesti.",
                    undefined_cols_msg = NULL)

            
   
#  2
test_function(name = "mean",
              args = c("x", "na.rm"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead  ülesandes 2  kasutama funktsiooni `mean`",
             args_not_specified_msg = paste("Määra `mean` käsus argumendi", c("`x`", "`na.rm`"), "väärtus."),
             incorrect_msg = paste("Muuda `merge` käsus argumendi", c("`x`", "`na.rm`"), "väärtust, see pole praegu korrektne.")) 

   
test_object("kesk",  
            undefined_msg = "Muutuja  `kesk` on defineerimata.",
            incorrect_msg = "Muutuja `kesk` väärtus ei ole korrektne. Proovi uuesti.") 
           
   
test_function(name = "sd",
              args = c("x", "na.rm"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead  ülesandes 2  kasutama funktsiooni `sd`",
             args_not_specified_msg = paste("Määra `sd` käsus argumendi", c("`x`", "`na.rm`"), "väärtus."),
             incorrect_msg = paste("Muuda `sd` käsus argumendi", c("`x`", "`na.rm`"), "väärtust, see pole praegu korrektne.")) 

   
test_object("stand",  
            undefined_msg = "Muutuja  `stand` on defineerimata.",
            incorrect_msg = "Muutuja `stand` väärtus ei ole korrektne. Proovi uuesti.") 
           
   
                        

success_msg("Hästi! Väike pingutus veel: kohe tuleb viimane ülesanne.")



```




--- type:NormalExercise lang:r xp:100 skills:3 key:cf82d267f7
## Andmestike ühendamine 2

Andmestike ühendamiseks nn võtmetunnuse kaudu saab kasutada käsku `merge`. 


Töölaual on olemas kaks andmestikku: 

- andmestikus `A` on kirjas vastajate id-kood, sugu, elukoht, vanus, pikkus, kaal, käte siruulatus ning arstivisiidi toimumine
- andmestikus `B` on kirjas vastajate id-kood, uuringugrupi tunnus ning vastused mitmesugustele testidele


*** =instructions

- **Ülesanne 1** Liida andmestikud id-koodi tunnuse põhjal, nimeta ühendatud andmestik nimega `uuring2`. Tulemuseks olevas andmestikus peaks olema ainult need uuritavad, kelle kohta on teada sugu, elukoht, vanus, pikkus, kaal, käte siruulatus,  arstivisiidi toimumine, uurignugrupi tunnus ning testitulemused. 

- **Ülesanne 2** Tekita liidetud andmestikku veel üks sootunnus `sugu2`: uuel tunnusel lisa sootunnuse koodidele sildid: kood `0` vastab naissoole, määra siia silt `Naine`, koodile `1` lisa silt `Mees`.

- **Ülesanne 3** Leia liidetud andmestiku korral uuringugrupi tunnuse ja soo sagedustabel, nii, et uurignugrupi tunnus määrab tabeli read. Kasuta seda sootunnust, mille tekitasid eelmises ülesandes. Omista tabel muutujale `tabel1`, prindi see tabel ekraanile.

- **Ülesanne 4** Kasutades eelnevalt leitud sagedustabelit leia tabel, kust oleks näha soo jaotus uuringugrupiti. Omista see muutujale `tabel2`, prindi ekraanile.

- **Ülesanne 5** Omista mutujale `c.naisi` naiste arv uuringugrupis `c`.




*** =hint
- Seda, millised objektid ühendatud andmestikku lähevad, reguleerivad käsu `merge()` argumendid `all, all.x, all.y`.
- Faktortunnuse tekitamiseks kasuta käsku `factor`, koodide siltidena määra vektor `c("Naine", "Mees")`.

*** =pre_exercise_code
```{r}
A <- read.csv2("http://kodu.ut.ee/~annes/R/A.csv", nrows = 45)
B <- read.csv2("http://kodu.ut.ee/~annes/R/B.csv", nrows = 160)
B <- B[, c("id", "grupp", sort(names(B)[-(1:2)]))]



```

*** =sample_code
```{r}
# Ülesanne 1: Liida andmestikud, tulemuses olgu kõik isikud kel on mõlemas andmestikus info olemas.
uuring2 <- merge(_____________________)

# Ülesanne 2: faktortunnuse loomine
uuring2$sugu2 <- _____(uuring2$sugu, labels = ________)

# Ülesanne 3: Sagedustebel
tabel1 <- table(_____, ______)


# Ülesanne 4: Jaotustabel
tabel2 <-  ______________



# Ülesanne 5: Naiste arv grupis c
c.naisi <- __________


```

*** =solution
```{r}
# Ülesanne 1:  Liida andmestikud, tulemuses olgu kõik isikud kel on mõlemas andmestikus info olemas.
uuring2 <-  merge(A, B, by = "id", all = FALSE)


# Ülesanne 2: faktortunnuse loomine
uuring2$sugu2 <- factor(uuring2$sugu, labels = c("Naine", "Mees"))


# Ülesanne 3: Sagedustabel
tabel1 <- table(uuring2$grupp, uuring2$sugu2)
tabel1

# Ülesanne 4: Jaotustabel
tabel2 <-  prop.table(tabel1, 1)
tabel2


# Ülesanne 5: Naiste arv grupis c
c.naisi <- 1

```



*** =sct
```{r}
test_predefined_objects("A", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `A`.", 
                        incorrect_msg = "Ära muuda andmestiku `A` sisu.")
 

test_predefined_objects("B", 
                        eq_condition = "equivalent",
                        eval = TRUE,
                        undefined_msg = "Ära kustuta andmestikku `B`.", 
                        incorrect_msg = "Ära muuda andmestiku `B` sisu.")


# 1
test_function(name = "merge",
              args = c("x", "y", "all"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead ülesandes   kasutama funktsiooni `merge`",
             args_not_specified_msg = paste("Määra `merge` käsus argumendi", c("`x`", "`y`", "`all`"), "väärtus."),
             incorrect_msg = paste("Muuda `merge` käsus argumendi", c("`x`", "`y`", "`all`"), "väärtust, see pole praegu õige.")) 

 

test_data_frame("uuring2", columns = c("id",  "vanus",    "elukoht" ,   "visiit" ,    "kasv",       "kaal",       "sirutus",    "grupp", "hinnang82" ,
 "hinnang86",  "hinnang90", "hinnang99",  "taust1" ,    "taust2"    , "taust3"   ,  "taust4" ),
                undefined_msg = "Andmestik `uuring2` on tekitamata!",
                undefined_cols_msg = "Andmestikust `uuring2` on mõni nõutud veerg puudu.",
                incorrect_msg = "Andmestikus `uuring2` on viga!")

        
        
#2        
test_function(name = "factor",
              args = c("x", "labels"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead ülesandes   kasutama funktsiooni `factor`",
             args_not_specified_msg = paste("Määra `factor` käsus argumendi", c("`x`", "`labels`"), "väärtus."),
             incorrect_msg = paste("Muuda `factor` käsus argumendi", c("`x`", "`labels`"), "väärtust, see pole praegu õige."))         
        
        
        
        
#3
test_function(name = "table",
              args = "...",
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead  ülesandes 2  kasutama funktsiooni `table`",
             args_not_specified_msg = paste("Määra `table` käsus argumendiks grupi ja soo tunnused."),
             incorrect_msg = c("Pane `table` käsus  esikohale grupitunnus ja teisele kohale soo tunnus `sugu2`.")) 

   
test_object("tabel1",  
            undefined_msg = "Muutuja  `tabel1` on defineerimata.",
            incorrect_msg = "Muutuja `tabel1` väärtus ei ole korrektne. Proovi uuesti.") 
           





            
 
#4
test_function(name = "prop.table",
              args = c("x", "margin"),
              index = 1,
             eq_condition = "equivalent",
             not_called_msg = "Pead  ülesandes 2  kasutama funktsiooni `prop.table`",
             args_not_specified_msg = paste("Määra `prop.table` käsus argumendi", c("`x`", "`margin`"), "väärtus."),
             incorrect_msg = c("Pane `prop.table` käsus  esiemseks argumendiks sagedustabel", "Pane `prop.table` käsus teiseks argumendiks  `margin = 1`")) 

   
test_object("tabel2",  
            undefined_msg = "Muutuja  `tabel2` on defineerimata.",
            incorrect_msg = "Muutuja `tabel2` väärtus ei ole korrektne. Proovi uuesti.") 
           
             
             
#5
 
test_object("c.naisi",  
            undefined_msg = "Muutuja  `c.naisi` on defineerimata.",
            incorrect_msg = "Muutuja `c.naisi` väärtus ei ole korrektne. vaata väärtust sagedustabelist") 
           
                        
             
 
            
            
            
            
success_msg("Tubli! Selleks korraks on ülesanded lahendatud.")

```
