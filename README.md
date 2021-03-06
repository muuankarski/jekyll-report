Alustava kuvaus
====================

Applikaation tarkoituksena on tarjota minimaalinen esimerkki "analyysiputkesta", joka analysoi datan ja raportoi tulokset staattisena verkkosivustona

Periaate on seuraava:

1. sovellus analysoi aineiston halutulla tavalla [R-ympäristössä](http://www.r-project.org/) käyttäen [knitr](http://yihui.name/knitr/)-teknologiaa ja 
2. tulostaa tulokset [jekyll](http://jekyllrb.com/)-pohjaiseen [bootstrap](http://getbootstrap.com/):llä muotoiltuun [staattiseen](http://fi.wikipedia.org/wiki/Verkkosivu#Staattiset_ja_dynaamiset_sivut) verkkosivustoon.
3. staattinen verkkosivusto on mahdollista julkaista verkossa tai paikallisesti

Pari linkkiä R:ään:

- [What is R by Revolution Analytics](http://www.revolutionanalytics.com/what-r)
- [RStudio](http://www.rstudio.com/)


### Prosessin teknisempi kuvaus

Prosessi etenee siis siten, että 

1. **_R** hakemiston [RMarkdown](http://www.rstudio.com/ide/docs/r_markdown) muotoiset analyysidokkarit käännettään `knitfiles.R`-skriptin avulla ns. blogipostauksiksi .markdown-muotoon **_posts**-kansioon, josta 
2. jekyll generoi ne automaattisesti .html-muotoon ja luo valmiin sivuston sisältöineen ja rakenteineen.
3. sovelluksen koodi on [git](http://git-scm.com/)-versionhallinnassa, mikä mahdollistaa kehityksen yhteistyössä ja sekä raportoinnin kätevän julkaisun verkossa.


Demo: Uusi projekti
======================

1. Kloonaa projektin pohja githubista
------------------

1. Avaa [RStudio](http://www.rstudio.com/ide/download/)
2. klikkaa **new project** oikeasta yläkulmasta
3. valitse **version control**
4. valitse **git**
5. kopio git-repon osoite URL-kenttään: `https://github.com/muuankarski/jekyll-report` ja annan projektille sopiva **nimi** ja osoita **kansio** jonne projekti perustetaan

2. Tee luo sivusto paikallisesti, tee analyysit ja päivitä sivustoa
------------------

1. Avaa **pääte** ja aja alla oleva komento **päätteessä**
    1. windows: `jekyll serve --watch`
    2. linux/OS X: `jekyll serve --watch --baseurl ''`
2. mene selaimella osoitteeseen `localhost:4000`
3. ajaa **R:ssä** komento `source("knitfiles.R")` ja päivitä selain - analyysit pitäisi ilmestyä saitille
4. tee muutoksia sivuille sekä analyysikoodiin tai muualle ja muutokset ilmestyvät selainta *päivittämällä*
5. Lopulta analyysit ovat valmiit ja sivusto valmis julkaistavaksi ja voit sulkea paikallisen sivuston **päätteessä** näppäinyhdistelmällä `Ctrl + c`

3. Julkaise sivusto Githubissa
------------------

1. luo uusi repository Githubissa esim. nimellä `uusiprojekti`. Sinulle luodaan uusi projekti jonka osoite on `https://github.com/kayttajatunnus/uusiprojekti`. **Tärkeää on muistaa että ko. projektin sivut näkyvät osoitteessa `https://kayttajatunnus.github.io/uusiprojekti`**
2. Muokkaa kahta tiedostoa **RStudiossa**: `_config.yml` ja `knitfiles.R`
    1. `_config.yml`: lisää sivujen url `"https://kayttajatunnus.github.io/uusiprojekti"` kohtaan `baseurl: ` (kaksoispisteen jälkeen)
    2. `knitfiles.R`: lisää sivujen url `"https://kayttajatunnus.github.io/uusiprojekti"` kohtaan `base.url="/"`
    3. **Huomaa jättää `/` url:n perään `knitfiles.R`-tiedostossa**
3. tuhoa kaikki .markdown tiedostot `_posts`-kansiosta
4. aja **R:ssä** komento `source("knitfiles.R")`  ja **päätteessä** komento: `jekyll build` ja sivusto on valmis verkkoon


### 3.1 Lisää uudet tiedostot ja muutokset paikallisesti git-repoon

1. lisää muutokset *staging area*lle **päätteessä** komennolla: `git add --all`
2. lisää muutokset paikalliseen versionhallintaan **päätteessä** komennolla: `git commit -m "viesti tulee tahan"`


### 3.2 Linkitä paikallinen projekti uuteen githubissa luomaasi projektiin

4. Aseta projektille uusi remote-osoite päätteessä viittaamaan uuteen luomaasi github-repoon **päätteessä** komennolla: `git remote set-url origin git@github.com:kayttajatunnus/uusiprojekti.git`
5. siirrä git-repo (versionhallinta) ensimmäistä kertaa uuteen github-repoon **päätteessä** komennolla: `git push -u origin master`


### 3.3 Tee julkaistuun prjektiin gh-pages haara (branch) jotta se näkyy webbisivuna

1. luo uusi branch nimeltä *gh-pages* **päätteessä** komennolla: `git branch gh-pages`
2. vaihda ko. branchiin **päätteessä** komennolla: `git checkout gh-pages`
3. julkaise branch githubiin **päätteessä** komennolla: `git push origin gh-pages`
4. 10 minuutin kuluessa sivut ovat näkyvissä osoitteessa: `kayttajatunnus.github.io/uusiprojekti/`


Ohjelmistoympäristö
======================

Analyysin ja julkaisu vaativat seuraavien ohjelmistojen asentamista

Versionhallinta eli alusta koko systeemille
------------------

- [git](http://git-scm.com/)

Analyysi
-------------------

- [R](http://www.r-project.org/) ja paketit:
    - `knitr`
    - `ggplot2`
    - `foreign`
    - `plyr`
    - `reshape2`
- Käyttöliittymä [RStudio](http://www.rstudio.com/ide/download/)

Julkaiseminen
--------------------

- [ruby](https://www.ruby-lang.org/en/) ja gemit
    - `jekyll`
    - `redcarpet`

Kaikki ohjelmistot ovat ilmaisia ja vapaita avoimen lähdekoodin ohjelmistoja ja siis lisensointuja vapaasti myös kaupalliseen käyttöön. Ohjelmistot toimivat niin Windows, linux kuin OS-X -käyttöjärjestelmissä.

TODO
======================

- analyysin pidemmälle menevä automatisaatio
- tiedonkeruun ja analyysin integroinnin mahdollisuudet
- esitysgrafiikka

