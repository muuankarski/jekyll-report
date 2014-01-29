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

Prosessi etenee siis siten, että 

1. **_R** hakemiston [RMarkdown](http://www.rstudio.com/ide/docs/r_markdown) muotoiset analyysidokkarit käännettään `knitfiles.R`-skriptin avulla ns. blogipostauksiksi .markdown-muotoon **_posts**-kansioon, josta 
2. jekyll generoi ne automaattisesti .html-muotoon ja luo valmiin sivuston sisältöineen ja rakenteineen.


Uuden projektin perustaminen, analyysit ja julkaisu githubissa
---------------------------

### Kloonaa projektin pohja githubista

1. Avaa [RStudio](http://www.rstudio.com/ide/download/)
2. klikkaa **new project** oikeasta yläkulmasta
3. valitse **version control**
4. valitse **git**
5. kopio git-repon osoite URL-kenttään: `https://github.com/muuankarski/jekyll-report` ja annan projektille sopiva **nimi** ja osoita **kansio** jonne projekti perustetaan

### Tee analyysit ja luo sivusto paikallisesti

1. ajaa R:ssä komento `source("knitfiles.R")`
2. Avaa pääte ja aja komento 
    1. windows: `jekyll serve --watch`
    2. linux/OS X: `jekyll serve --watch --baseurl ''`
3. mene selaimella osoitteeseen `localhost:4000`
4. tee muutoksia sivuille sekä analyysikoodiin tai muualle ja muutokset ilmestyvät selainta *päivittämällä*
5. Lopulta analyysit ovat valmiit ja sivusto valmis julkaistavaksi ja voit sulkea paikallisen sivuston päätteessä näppäinyhdistelmällä `Ctrl + c`

### Julkaise sivusto Githubissa

1. luo uusi repository Githubissa esim. nimellä `uusiprojekti`. Sinulle luodaan uusi projekti jonka osoite on `https://github.com/kayttajatunnus/uusiprojekti`. **Tärkeää on muistaa että ko. projektin sivut näkyvät osoitteessa `https://kayttajatunnus.github.io/uusiprojekti`**
2. Muokkaa kahta tiedostoa: `_config.yml` ja `knitfiles.R`
    1. `_config.yml`: lisää sivujen url `"https://kayttajatunnus.github.io/uusiprojekti"` kohtaan `baseurl: ` (kaksoispisteen jälkeen)
    2. `knitfiles.R`: lisää sivujen url `"https://kayttajatunnus.github.io/uusiprojekti"` kohtaan `base.url="/"`
    3. **Huomaa jättää `/` url:n perään `knitfiles.R`-tiedostossa
3. aja **R:ssä** komento `source("knitfiles.R")`  ja **päätteessä** komento `jekyll build` ja sivusto on valmis verkkoon

#### Lisää uudet tiedostot ja muutokset paikallisesti git-repoon

1. lisää muutokset *staging area*lle komennolla `git add --all`
2. lisää muutokset paikalliseen versionhallintaan `git commit -m "viesti tulee tähän"`

#### Linkitä paikallinen projekti uuteen githubissa luomaasi projektiin

4. Aseta projektille uusi remote-osoite päätteessä viittaamaan uuteen luomaasi github-repoon komennolla `git remote set-url origin git@github.com:kayttajatunnus/uusiprojekti.git`
5. siirrä git-repo (versionhallinta) ensimmäistä kertaa uuteen github-repoon komennolla `git push -u origin master`

#### Tee julkaistuun prjektiin gh-pages haara (branch) jotta se näkyy webbisivuna

1. luo uusi branch nimeltä `gh-pages` komennolla: `git branch gh-pages`
2. vaihda ko. branchiin komennolla `git checkout gh-pages`
3. julkaise branch githubiin komennolla `git push origin gh-pages`
4. 10 minuutin kuluessa sivut ovat näkyvissä osoitteessa: `kayttajatunnus.github.io/uusiprojekti/`


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

