Installation locale

-----------------------------------------------------------------------------------------------------------------------------------------------

Télécharger Xampp : https://www.apachefriends.org/download.html, Choisissez la version qui correspond à votre système.
Durant l'installation de Xampp faites simplement next en laissant les choix par default.

(Si jamais le logiciel à du mal se lancer, lancez le en administrateur)
->Une fois installé aller dans config (en haut à droite de la fenetre Xampp): cocher Apache / Mysql
->Normalement php est installé en meme temps que xampp mais il se peut que vous deviez allez l'activer dans les variables d'environements de votre système,
aller dans votre menu démarrer et tapez path, vous verrez "Modifier les variables d'environements" cliquez dessus. 
Une fenetre va s'ouvrir et sur la premiere page cliquez sur " Variables d'environements ".
Ensuite choisissez entre variable utilisateurs ou systeme -> Path -> Modifier -> ajouter la route (chemin absolu) vers xampp/php
enfin on valide les changements et on relance xampp (attention pensé à fermé xampp en bas à droite dans les tache car ça m'est arrivé qu'il plante quand on le ferme mal
créant des erreurs par la suite et forcé la réinstallation)
relancer votre invite de commande pour qu'il prenne la modifcation et verifier que php est bien installer avec la commande : php -v

Rendez-vous sur gitHub pour télécharger mon projet ou le cloner.
Une fois acquis, placez le dans le dossier htdocs de xampp, (vous pouvez supprimer ce qui est dans ce dossier avant de mettre le projet dedans).
Lancez le dans votre editeur de code.
lancer le terminal depuis le dossier racine et installer composer :

php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'edb40769019ccf227279e3bdd1f5b2e9950eb000c3233ee85148944e555d97be3ea4f40c3c2fe73b22f875385f6a5155') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"

Puis pour avoir accès à un server local rapidement, installer symfony cli :
scoop install symfony-cli

Exécutez la commande suivante pour installer les dépendances du projet : 
composer install

vous pouvez verifier si symfony est prêt sur votre ordinateur avec la commande de symfony CLI : symfony check:requirements

Copiez le fichier .env en un nouveau fichier .env.local et configurez la connexion à la base de données dans ce dernier.
Exécutez la commande pour créer la base de données :

php bin/console doctrine:database:create
Ensuite, effectuez les migrations pour créer les tables de la base de données :

php bin/console doctrine:migrations:migrate

Lancez le serveur Symfony :
Exécutez la commande suivante pour démarrer le serveur de développement Symfony :

symfony server:start

Une URL, généralement http://localhost:8000, devrait apparaitre dans la console.

Accédez à votre application en ouvrant votre navigateur web et accédez à l'URL indiquée par le serveur Symfony.

référence des installations : 

Xampp : https://www.apachefriends.org/download.html, Choisissez la version qui correspond à votre système.
Composez : https://getcomposer.org/download/
symfony CLI :https://symfony.com/download
symfony : https://symfony.com/doc/current/setup.html

-----------------------------------------------------------------------------------------------------------------------------------------------

Création du compte admin:

Pensez à compléter le .env avec la connexion à la base de donnée. J'ai laissé ma connexion de base qui correspond à un environement local.

Ensuite une fois que l'accès base de données est configuré, vous pouvez, avec la commande : php bin/console d:m:m
la préparer.

Vous pouvez lancer la commande : php bin/console doctrine:fixtures:load
le compte admin sera auto généré :

email : garagevparrot@garage.pr
mot de passe : admin

vous avez aussi accès à un compte utilisateur/employé
email : employeeparrot@garage.pr
mot de passe : admin

-----------------------------------------------------------------------------------------------------------------------------------------------

(pour ce qui est de la création sur le site en ligne, elle se fait en passant directement par la base de données,
et en insérant le un password hashé que j'ai stocké au préalable quelques part. Rappel il n'y qu'un seul compte admin sur le site donc je ne préfére pas rajouter de fonction pour setup l'admin depuis le code.)
