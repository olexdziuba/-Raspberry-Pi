# Installation et configuration Pi Hole sur Raspberry Pi

Pi Hole vous permet de bloquer la publicité et le pistage sur internet (trackers) au niveau DNS. Par exemple, environ 43% du trafic est bloqué sur mon réseau domestique. Même une partie  de la publicité YouTube sur un téléviseur intelligent est bloquée, mais pas beaucoup car le blocage au niveau DNS a ses limites.
.

 <img src="/images/pihole_img12.png">

Pour installer Pi-Hole, j’utilise Raspberry Pi Zéro, parce que sa puissance est suffisante pour le serveur DNS. Par exemple voici le nombre de ressources utilisées sur le mien Raspberry Pi Zéro:

 <img src="/images/pihole_img16.png">

Configuration:

-   Raspberry Pi connecté par un câble à votre routeur (la connexion est plus stable que le wifi, peut être aurez vous besoin d’un adaptateur USB-LAN)
-   installation minimale raspbian
-   connection ssh
-    IP: 192.168.0.11

Avant l’installation il faut configurer l’adresse IP. Il est préférable de choisir une adresse IP parmi les adresses réservées comme statiques pour ne pas avoir  de conflits à l'avenir.

## Installation Pi Hole

Premièrement il faut  faire une mise à jour de votre système:

`sudo apt-get update -y`

`sudo apt-get upgrade -y`

Faire l'installation Pi-hole en utilisant:

`wget -O basic-install.sh https://install.pi-hole.net`

`sudo bash basic-install.sh`

OU

 `sudo curl -sSL https://install.pi-hole.net | bash`

 <img src="/images/pihole_img13.png">

 <img src="/images/pihole_img4.png">

Il faut accepter la transformation raspberry pi in network-wide ad blocker. C'est pourquoi il est préférable d’utiliser un appareil séparé.

 <img src="/images/pihole_img3.png">

La fenêtre suivante vous propose de soutenir financièrement le projet. 

<img src="/images/pihole_img20.png">

Ici il faut accepter la configuration de l’adresse IP statique:

 

 <img src="/images/pihole_img10.png">

La prochaine étape est le choix du fournisseur  DNS . J’utilise Cloudflare, parce qu’il est[ plus
rapide](https://medium.com/@nykolas.z/dns-resolvers-performance-compared-cloudflare-x-google-x-quad9-x-opendns-149e803734e5&sa=D&ust=1597681316391000&usg=AOvVaw3v7XWIFmwNDYmpFQ0hl8Ud) que les autres.

 <img src="/images/pihole_img11.png">

Prochaine étape: le choix du block listé. Vous devez tout sélectionner car c'est le niveau minimum de blocage. Ensuite, nous ajouterons plus de blocks listés.

 <img src="/images/pihole_img7.png">

Il faut choisir IPV4 et IPV6

 <img src="/images/pihole_img5.png">

Après Il  faut accepter l’adresse IP statique:

 <img src="/images/pihole_img9.png">

 <img src="/images/pihole_img1.png">

 <img src="/images/pihole_img15.png">

Il faut installer l’interface web admin  pour accéder à partir d'un navigateur Web

 <img src="/images/pihole_img19.png">

On accepte aussi l’installation du serveur web pour avoir accès à l’interface  web à partir d'un navigateur Web

 <img src="/images/pihole_img18.png">

Dans la prochaine étape on choisit l’acceptation d’écriture  log file. Si on utilise Raspberry pi avec micro SD carte, c’est préférable de choisir “OFF”, sinon un écrasement fréquent de la carte mémoire réduira sa durée de vie.

 <img src="/images/pihole_img2.png">

Dans la prochaine étape je choisis Anonymus mode

 <img src="/images/pihole_img17.png">

Finalement, l’installation finie. Pi hole montre l’adresse IP, l’accès à  l’interface  web et mot de passe. Il faut copier et sauvegarder cette information.

 <img src="/images/pihole_img6.png">

Après vous devrez fournir l'adresse IP de votre serveur Pi-Hole à la place des adresses IP du serveur DNS dans votre routeur. La plupart des appareils proposent deux options répertoriant au moins deux serveurs de noms DNS, vous fournirez une adresse IP DNS et laissez l'autre (reste) vide. Si vous spécifiez une deuxième adresse IP DNS qui n'est pas un serveur PiHole, le blocage des publicités ne fonctionnera pas sur certains appareils.

## Ajouter plus de blocks lists

L'installation initiale ne fournit que le blocage des publicités de
base. Si vous souhaitez bloquer plus d'annonces, vous devez ajouter
d'autres listes de blocage. Ici, vous devez faire attention car vous
pouvez perdre l'accès à de nombreux sites nécessaires :)

J'utilise les listes que j'ai trouvées sur GitHub
[https://github.com/jerryn70/GoodbyeAds](https://www.google.com/url?q=https://github.com/jerryn70/GoodbyeAds&sa=D&ust=1597681316397000&usg=AOvVaw2PjJlM6DWGnMW8wjVfQqL2)

Pour ajouter une nouvelle blocklist il faut copier l'adresse sur list en
format txt, par exemple ici:

 <img src="/images/pihole_img14.png">

Après il faut aller dans le Group Management -\> Adlist de votre Pi-hole, ajouter lien sur file de blocklist et appuyez sur Add.

 <img src="/images/pihole_img8.png">

Si vous devez exclure un site de blocage, vous pouvez l'ajouter à Whitelist.

À mon avis, le blocage des publicités est un jeu de chat et de souris :)

Bonne chance!

## Quelques liens pour aller plus loin avec Pi-hole et mes sources d’inspiration:

[https://docs.pi-hole.net/core/pihole-command/](https://www.google.com/url?q=https://docs.pi-hole.net/core/pihole-command/&sa=D&ust=1597681316399000&usg=AOvVaw2B-q77qjukCTAw-chOqC5v)

[https://github.com/Prowler2/PiHole](https://www.google.com/url?q=https://github.com/Prowler2/PiHole&sa=D&ust=1597681316400000&usg=AOvVaw0e1yugyHwKPLLytm07M8L2)

[https://www.smarthomebeginner.com/pi-hole-setup-guide/](https://www.google.com/url?q=https://www.smarthomebeginner.com/pi-hole-setup-guide/&sa=D&ust=1597681316400000&usg=AOvVaw0Ljqj5hPoE8hmKnKa1hs9P)

[https://github.com/pi-hole/pi-hole/\#one-step-automated-install](https://www.google.com/url?q=https://github.com/pi-hole/pi-hole/%23one-step-automated-install&sa=D&ust=1597681316401000&usg=AOvVaw1DKCmXF5oMQt3SvBr0uFyy)

[https://github.com/jerryn70/GoodbyeAds](https://www.google.com/url?q=https://github.com/jerryn70/GoodbyeAds&sa=D&ust=1597681316401000&usg=AOvVaw1JNbgHfzIl2aA98QoSamHZ)

[https://medium.com/@nykolas.z/dns-resolvers-performance-compared-cloudflare-x-google-x-quad9-x-opendns-149e803734e5](https://www.google.com/url?q=https://medium.com/@nykolas.z/dns-resolvers-performance-compared-cloudflare-x-google-x-quad9-x-opendns-149e803734e5&sa=D&ust=1597681316402000&usg=AOvVaw2T9ZE9Q7cHi8E2tFcHWnsf)

 


