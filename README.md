# Alustava kuvaus

Projektin tarkoituksena on automatisoida määrämuotoisen datan analysointia ja raportointia R-kielen avulla.

## Toteutus

Tässä toteutuksessa analyysiprosessin automatisointia on kirjoitettu esimerkinomaisesti alkuun. Analyysiteknologian vaihtamisen ohella on tässä keskitytty tulosten julkaisumuotoon. Paperiorientoitunut .pdf -vyyhti on korvattu staattisella mobiililaitteissa skaalautuvalla verkkosivustolla.

Toisin sanoen periaate on seuraava:

1. sovellus analysoi aineiston halutulla tavalla [R-ympäristössä](http://www.r-project.org/) ja 
2. tulostaa tulokset [jekyll](http://jekyllrb.com/)-pohjaiseen [bootstrap](http://getbootstrap.com/):llä muotoiltuun [staattiseen](http://fi.wikipedia.org/wiki/Verkkosivu#Staattiset_ja_dynaamiset_sivut) verkkosivustoon.

Verkkosivusto voidaan näyttää asiakkaalle joko www-palvelimen kautta, toimittaa paikalisesti toimivana saittina joko sähköpostilla tai fyysisellä medialla.

Verkkosivustolla on monia muitakin etuja, joita johtopäätökset sivulla on demottu mm. vuorovaikutteisen analyysiympäristön ja grafiikan muodossa.

## Uuden projektin perustaminen

1. Avaa pääte ja kloonaa repo Githubista komennolla: `git clone keva-demo`
2. `cd `
3. lisää _config.yal tiedostoon rivi `baseurl: saittisi.url` ja lisää sama url myös tiedoston `knitfiles.R` `base.url="/"`kohtaan.
3. Aja komento `R CMD BATCH knitfiles.R` ja R tekee analyysit ja generoi postit
3. Aja komento `jekyll serve --watch --baseurl ''` ja jekyll luo sivuston paikallisesti
4. avaa selaimessa osoite [localhost:4000](localhost:4000)
5. Tuloksena projekti oletussisällöllä paikalisesti
6. julkaise projekti

Prosessi etenee siis siten, että **_R** hakemiston [RMarkdown](http://www.rstudio.com/ide/docs/r_markdown) muotoiset analyysidokkarit käännettään `knitfiles.R`-skriptin avulla ns. blogipostauksiksi .markdown-muotoon **_posts**-kansioon, josta jekyll generoi ne automaattisesti .html-muotoon ja luo valmiin sivuston sisältöineen ja rakenteineen.


# Ohjelmistoympäristö

Analyysin ja julkaisu vaativat seuraavien ohjelmistojen asentamista
- [R]() ja paketit
    - [knitr]()
    - [ggplot2]()
    - [foreign]()
    - [plyr]()
    - [reshape2]()
- [RStudio]()

- [ruby](https://www.ruby-lang.org/en/) ja gemit
    - [jekyll]()

- [git](http://git-scm.com/)

Kaikki ohjelmistot ovat ilmaisia ja vapaita avoimen lähdekoodin ohjelmistoja ja siis lisensointuja vapaasti myös kaupalliseen käyttöön. Ohjelmistot toimivat niin Windows, linux kuin OSX -käyttöjärjestelmissä.

# TODO
- analyysin pidemmälle menevä automatisaatio
- tiedonkeruun ja analyysin integroinnin mahdollisuudet
- esitysgrafiikka

