# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

REPONSE a) Niveau facile
    Quel est le nombre total d'objets Album contenus dans la base (sans regarder les id bien sûr) ?'
==> Album.count : 347 album

    Qui est l'auteur de la chanson "White Room" ?'
==> Track.find_by(title: "White Room")
    #<Track id: 505, title: "White Room", album: "The Cream Of Clapton", artist: "Eric Clapton", duration: 301583, size: 9872606, price: 0.99, created_at: "2019-08-01 03:51:44", updated_at: "2019-08-01 03:51:44">
   l'auteur' est Eric Clapton

    Quelle chanson dure exactement 188133 milliseconds ?
==> Track.find_by(duration: 188133)
   #<Track id: 40, title: "Perfect", album: "Jagged Little Pill", artist: "Alanis Morissette", duration: 188133, size: 6145404, price: 0.99, created_at: "2019-08-01 03:50:10", updated_at: "2019-08-01 03:50:10">
   la chanson est "Perfect"
    Quel groupe a sorti l'album' "Use Your  II" ?
==> Album.find_by(title: "Use Your Illusion II")
   #<Album id: 92, title: "Use Your Illusion II", artist: "Guns N Roses", created_at: "2019-08-01 03:49:09", updated_at: "2019-08-01 03:49:09">
   l'artist' est "Guns N Roses"
b) Niveau Moyen

    Combien y a t'il d'albums dont le titre contient "Great" ? (indice)
==> Album.where("title like?", "%Great%").count
   13 titres

    Supprime tous les albums dont le nom contient "music".
==>  methode par boucles 
    a = Album.where("title like?", "%music%") # on a 4 elements
    a.length.times do |i|
    a[i].destroy
    end

    Combien y a t'il d'albums écrits par AC/DC ?
==> Album.where("artist like?", "%AC/DC%").count
   2 albums

    Combien de chanson durent exactement 158589 millisecondes ?
==>  Track.where("duration like?", "%158589%").count
   0 chason

c) Niveau Difficile

Pour ces questions, tu vas devoir effectuer des boucles dans la console Rails. C'est peu commun mais c'est faisable, tout comme dans IRB.
 
    puts en console tous les titres de AC/DC.
==> a = Track.where(artist:"AC/DC")
    a.length.times do |i|
    puts a[i].title
    end
    18 titres s'affiche'


    puts en console tous les titres de l'album' "Let There Be Rock".
==> b = Track.where(album: "Let There Be Rock") 
    b.length.times do |i|
    puts b[i].title
    end
    8 titres

    Calcule le prix total de cet album ainsi que sa durée totale.
==> Sa durée   
    a = 0
    b.length.times do |i|
    a += b[i].duration
    end
    puts a ===>  2453259
==> prix total
    b.length.times do |i|
    a += b[i].price
    end
    puts a  ===> 0.99

    Calcule le coût de l'intégralité' de la discographie de "Deep Purple".
==> 91 titres
    c = 0
    a.length.times do |i|
    c += a[i].price
    end
    puts c ===> 90.90


    Modifie (via une boucle) tous les titres de "Eric Clapton" afin qu'ils soient affichés avec "Britney Spears" en artist'.
==>  32 titres

    a=Track.where(artist: "Eric Clapton")
    a.length.times do |i|
    a[i].update(title: a[i].title + " "+"Britney Spears")
    end
