Alustava kuvaus
====================

Projektin tarkoituksena on automatisoida määrämuotoisen datan analysointia ja raportointia R-kielen avulla.

Idea
--------------------

Periaate on seuraava:

1. sovellus analysoi aineiston halutulla tavalla [R-ympäristössä](http://www.r-project.org/) ja 
2. tulostaa tulokset [jekyll](http://jekyllrb.com/)-pohjaiseen [bootstrap](http://getbootstrap.com/):llä muotoiltuun [staattiseen](http://fi.wikipedia.org/wiki/Verkkosivu#Staattiset_ja_dynaamiset_sivut) verkkosivustoon.

### Miksi verkkosivusto eikä paperinippua

Verkkosivusto voidaan näyttää joko www-palvelimen kautta, toimittaa paikalisesti toimivana saittina joko sähköpostilla tai fyysisellä medialla. Verkkosivustolla on monia muitakin etuja, joita johtopäätökset sivulla on demottu mm. vuorovaikutteisen analyysiympäristön ja grafiikan muodossa.

### Prosessin teknisempi kuvaus

Prosessi etenee siis siten, että **_R** hakemiston [RMarkdown](http://www.rstudio.com/ide/docs/r_markdown) muotoiset analyysidokkarit käännettään `knitfiles.R`-skriptin avulla ns. blogipostauksiksi .markdown-muotoon **_posts**-kansioon, josta jekyll generoi ne automaattisesti .html-muotoon ja luo valmiin sivuston sisältöineen ja rakenteineen.


Uuden projektin perustaminen, analyysit ja julkaisu githubissa
---------------------------

### Kloonaa projektin pohja githubista

1. Avaa [RStudio](http://www.rstudio.com/ide/download/)
2. klikkaa **new project** oikeasta yläkulmasta
3. valitse **version control**
4. valitse **git**
5. kopio git-repon osoite URL-kenttään: `https://github.com/muuankarski/jekyll-report` ja annan projektille sopiva nimi ja kansio jonne se tulee

### Tee analyysit ja luo sivusto paikallisesti

1. ajaa R:ssä komento `source("knitfiles.R")`
2. Avaa pääte ja aja komento `jekyll watch --serve --baseurl ''`
3. mene selaimella osoitteeseen `localhost:4000`

### Julkaise sivusto Githubissa

1. luo uusi repository Githubissa esim. nimellä `uusiprojekti`. Sinulle luodaan uusi projekti jonka osoite on `https://github.com/kayttajatunnus/uusiprojekti`
2. Korvaa `/` projektin urlilla sekä **_config.yal**-tiedoston `baseurl: /` että **knitfiles.R**-tiedoston  `base.url="/"`kohdissa.
3. aja komennot `source("knitfiles.R")` R:ssä ja komento `jekyll build` päätteessä vielä toistamiseen

#### Lisää uudet tiedostot ja muutokset paikallisesti git-repoon

1. lisää muutokset *staging area*lle komennolla `git add --all`
2. lisää muutokset paikalliseen versionhallintaan `git commit -m "viesti tulee tähän"`

#### Linkitä paikallinen projekti uuteen githubissa luomaasi projektiin

4. Aseta projektille uusi remote-osoite päätteessä viittaamaan uuteen luomaasi github-repoon komennolla `git remote set-url origin git@github.com:kayttajatunnus/uusiprojekti.git`
5. siirrä versionhallinta ensimmäistä kertaa uuteen repoon komennolla `git push -u origin master`

#### Tee julkaistuun prjektiin gh-pages haara (branch) jotta se näkyy webbisivuna

Voit tehdä tämän joko githubissa tai paikallisesti koneella

1. **GitHubissa**: mene selaimella repoon githubissa ja luo uusi branch valikosta nimellä `gh-pages`.
2 **paikallisesti koneella**:
    1. Luo uusi branch komennolla `git branch gh-pages`
    2. vaihda ko. branchiin komennolla `git checkout gh-pages`
    3. julkaise branch githubiin komennolla `git push origin gh-pages`
3. 10 minuutin kuluessa sivut ovat näkyvissä osoitteessa: `kayttajatunnus.github.io/uusiprojekti/`


Ohjelmistoympäristö
======================


Analyysin ja julkaisu vaativat seuraavien ohjelmistojen asentamista
- [R]() ja paketit
    - `knitr`
    - `ggplot2`
    - `foreign`
    - `plyr`
    - `reshape2`
- [RStudio](http://www.rstudio.com/ide/download/)

- [ruby](https://www.ruby-lang.org/en/) ja gemit
    - [jekyll]()

- [git](http://git-scm.com/)

Kaikki ohjelmistot ovat ilmaisia ja vapaita avoimen lähdekoodin ohjelmistoja ja siis lisensointuja vapaasti myös kaupalliseen käyttöön. Ohjelmistot toimivat niin Windows, linux kuin OSX -käyttöjärjestelmissä.

TODO
======================

- analyysin pidemmälle menevä automatisaatio
- tiedonkeruun ja analyysin integroinnin mahdollisuudet
- esitysgrafiikka

