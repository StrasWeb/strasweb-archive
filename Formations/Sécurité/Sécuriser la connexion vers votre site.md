# Sécuriser la connexion vers votre site

Par défaut, le protocole HTTP utilisé par les navigateurs n'est pas sécurisé, ce qui signifie que n'importe qui espionnant votre connexion peut voir tout ce que vous transmettez. Il est donc relativement facile de récupérer les mots de passe des autres internautes sur un réseau wi-fi public s'ils se connectent à des site en HTTP non-sécurisés. (Il existe des outils comme [Firesheep](http://codebutler.github.com/firesheep/) qui rendent cela très facile.)

C'est pourquoi le protocole HTTPS a été créé en 1994 afin d'éviter ce genre de problème. HTTPS utilise le protocole SSL et un certificat numérique pour vérifier l'identité du site et chiffrer la connexion entre le navigateur et le serveur.

Votre navigateur vous signale généralement qu'un site utilise HTTPS en affichant un petit cadenas ou le nom du site en bleu/vert. (Le vert indique un certificat de classe 3, qui certifie que l'identité de l'entreprise a été dûment vérifiée.)

Cependant, ce certificat ayant un coût, HTTPS est loin d'être utilisé par défaut sur la majorité des sites. Jusqu'il y a peu, même Facebook n'activait pas HTTPS par défaut !

Mais nous allons voir que des solutions gratuites existent et que, si la sécurité de vos utilisateurs vous tient à cœur, il n'est pas si difficile de mettre en place HTTPS sur votre site.

## Comment ça marche ?

Lors que vous vous connectez à un site en HTTPS, le navigateur reçoit le certificat du site et vérifie qu'il est valide. Ce certificat a été préalablement signé par une autorité de certification et votre navigateur ne peut le vérifier que si cette autorité de certification est dans sa liste de confiance.

Le problème c'est que ces autorités de certification vendent généralement ces certificats au prix fort.

Il est, en théorie, possible de signer vous-même le certificat ou d'utiliser une autorité de certification gratuite comme [CAcert](http://www.cacert.org/), mais le certificat ne pourra pas être vérifié par le navigateur et vos visiteurs auront droit à une énorme erreur effrayante. Autant dire que cela fera fuir la grosse majorité de vos visiteurs.

## Comment faire alors ?

Heureusement, il existe une autorité de certification qui délivre des certificats gratuits. Il s'agit de [StartSSL](https://startssl.com/). Vous pouvez demander en quelques clics un certificat valide reconnu par tous les navigateurs.

Attention cependant si votre site utilise des sous-domaines (''blog.strasweb.fr'' est par exemple un sous-domaine de ''strasweb.fr''), il vous faudra un certificat par sous-domaine. De plus, les certificats sont à renouveler tous les ans, ce qui peut être contraignant si vous avez beaucoup de domaines.

## Mettre en place le certificat

La plupart des serveurs Web ont dans leur documentation un chapitre consacré à HTTPS. Cependant, si l'administration de serveur n'est pas votre tasse de thé, il est possible que votre hébergeur propose de vous installer un certificat (moyennant finance, bien entendu). Vous pouvez également demander à StrasWeb de vous donner un coup de main !

Voici un exemple basique de configuration pour Apache :

```apache
Listen 443
SSLEngine on
SSLCertificateFile /etc/apache2/rudloff.crt
SSLCertificateKeyFile /etc/apache2/server.key
SSLCACertificateFile /etc/apache2/ca.pem
```

Il suffit en fait simplement d'ouvrir le port 443 (le port par défaut pour HTTPS), d'activer SSL et d'indiquer le certificat, la clef (Il est possible que vous disposiez déjà d'une clef sur votre serveur, sinon StartSSL peut en générer une pour vous.), ainsi que le certificat de l'autorité de certification. (Celui de StartSSL est disponible [ici](http://www.startssl.com/certs/ca.pem ).)
