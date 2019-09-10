# TP 1 - Installation d’Ubuntu Server et prise en main du shell

<ol>
<h2> Manuel</h2>
<li> A l’aide du manuel, identifiez le rôle de la commande which</li>
*wich renvoie le chemin des fichiers*

 >` # man which`


<li>Quand on consulte cette page, comment peut-on rechercher, par exemple, le mot option?</li>

 >` #[wich] -a nom-du-fichier || -a option`
<li> Comment quitte-t-on le manuel?</li>

 >` (press h to help and q to quit)`

<li>Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la première page de la section 6; de quoi parle cette section
</li>

 *sectrion 6 : describes the games and funny  little programs available on the system*

 >`#man 6 intro`
</ol>
<ol>
<h2> Navigation dans l’arborescence des fichier</h2>
 <li>allez dans le dossier /var/log</li>

 >`#cd ../../var/log`

 <li>remontez dans le dossier parent (/var) en utilisant un chemin relatif</li>

 >`#cd ..`

  <li>retournez dans le dossier personnel</li>

   >`#cd ../../home`

<li>. revenez au dossier précédent (/var)</li>

   >`#cd /var`


<li>essayez d’accéder au dossier /root; que se passe-t-il?</li>

*je n'est pas la permition*

<li>essayez la commande sudo cd /root; que se passe-t-il? Expliquez</li>

*commande n' éxiste pas car cd n'est pas un programme mais une commande intégrer(sudo ne s'applique qu'au programme)*

<li> à partir de votre dossier personnel, créez l’arborescence suivante </li>

 >`#sudo mkdir dossier1`
 >`#sudo mkdir dossier2`
 >`#cd dossier2`
 >`#sudo mkdir dossier2.1`
 >`#sudo mkdir dossier2.2`

 >`#cd dossier2.2`
 >`#sudo touch fichier2`
 >`#sudo touch fichier3`

>`#cd ../../dossier1`
>`#sudo touch fichier1`

<li> revenez dans votre dossier personnel; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1; que se passe-t-il?</li>

>`#cd ..`
>`#cd dossier1`
>`# sudo rm fichier1`
>`#cd ..`
>`# sudo rm dosssier1`

*impossible de le suprimmer c'est un dossier*
 <li>
 quelle commande permet de supprimer un dossier?
 </li>

>`# sudo rmdir dosssier1`

<li>
que se passe-t-il quand on applique cette commande à Dossier2?
</li>

*il dit que le dosssier n'est pas vide donc impossible a supprimer*

<li>
comment supprimer en une seule commande Dossier2 et son contenu
</li> 

>`# sudo rm -r dossier2`

</ol>
<ol>
<h2>Commandes importantes</h2>
<li>
Quelle commande permet d’aﬀicher l’heure? A quoi sert la commande time?
</li>

>`# sudo date`

*[sudo] password for exst:
lundi 9 septembre 2019, 15:09:07 (UTC+0000)*

*time determines which information to display about the resources used by the COMMAND from the string FORMAT*

<li>
Dans votre dossier personnel, tapez successivement les commandes ls puis la; que peut-on en déduire sur les fichiers commençant par un point
</li>

*Lister les fichiers et dossiers présents dans un répertoire*

>`# ls`

*dossier1 exist*

>`# la`

*dossier1 exist*

*que les fichiers commençant par un point sont des fichiers cachés*
<li>
Où se situe le programme ls?
</li>

<li>Que fait la commande ll? (indice : la commande alias peut vous aider</li>

>`# alias ll='ls -a'`
*ls  -a  : liste tout le contenu d’un répertoire, c’est-à-dire également les dossiers cachés commençant par un point. par exemple : /home/ordinosor/.config ; en mode graphique, cela correspond en quelque sorte, à presser la combinaison de touches Ctrl + H. Si vous faites ça dans votre gestionnaire de fichiers thunar ou pcman, vous allez faire apparaître ou disparaître les dossiers cachés.*

<li>Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ?</li>

>`# cat bin`
>`# ls bin`

<li>. Que fait la commande ls .. ?</li>
*affiche le contenu du répertoire *

<li>Quelle commande donne le chemin complet du dossier courant ?</li>

>`# ls find / -name ou pwd`

<li>Que fait la commande echo 'yo' > plop exécutée 2 fois ?</li>

*sa écrit/ affiche echo dans le ficchier redirige et ne l'écrase pas  si existe (écris a la ligne)*
*ecris mais sa n'efface pas se qu'il y avais avant*

<li> Que fait la commande echo 'yo' >> plop exécutée 2 fois ?</li>
*sa écrit/ affiche echo dans le ficchier redirige puis redirigier dans le dossier d'après  et l'écrase si existe*
*ecris mais sa efface se qu'il y avais avant*

<li>A quoi sert la commande file ? Essayez la sur des fichiers de types différents</li>
*Fonction : déterminer le type de fichier*
<li>
Créez un fichier toto qui contient la chaîne Hello Toto ! ; créer ensuite un lien titi vers ce fichier
avec la commande ln toto titi. Modifiez à présent le contenu de toto et affichez le contenu de titi :
qu’observe-t-on ? Supprimez le fichier toto ; quelle conséquence cela a-t-il sur titi ?
</li>
*ln Crée un lien (physique ou symbolique) vers un fichier (ou un répertoire)*
*si on supprime le dossier originel ou ponte le lien ici (hello toto) tout les fichier utilisant se liens n'afficheront plus hello toto*

<li> Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le
contenu de titi ; quelle conséquence pour tutu ? Et inversement ? Supprimez le fichier titi ; quelle
conséquence cela a-t-il sur tutu ?</li>

>`ln -s Rep1/Rep2/Monfichier MonLien `*Crée un lien symbolique MonLien de Rep1/Rep2/Monfichier dans le répertoire où on se trouve*
*cela ne supprime pas le texte*

<li>Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et
reprendre le défilement à l’écran ?</li>

>`  Ctrl+C pour stopper la commande`
>`  Ctrl+D pour fermer le terminal`

<li>Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les
lignes 10 à 20.
</li>

>`head -n 5 `
>`head -n 15 `
>`head -n 10,25 `
>`tail = fur et a mesure `

<li>Que fait la commande dmesg | less ? </li>

>`less dossier1 `
*afficher le fichier page par page*

<li>Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page
de manuel de ce fichier ?</li>

*contient différentes informations sur les comptes utilisateurs. Ces
       informations consistent en sept champs séparés par des deux-points (« : ») :

       ·   nom de connexion de l'utilisateur (« login »)

       ·   un mot de passe chiffré optionnel

       ·   l'identifiant numérique de l'utilisateur

       ·   l'identifiant numérique du groupe de l'utilisateur

       ·   le nom complet de l'utilisateur ou un champ de commentaires

       ·   le répertoire personnel de l'utilisateur

       ·   l'interpréteur de commandes de l'utilisateur (optionnel)*
>`less passwd `
>`cat passwd `

<li>Affichez seulement la première colonne triée par ordre alphabétique inverse</li>

>`#sort -t: -k 3,3  ou  sort -n -t/ +0d -1 +3 +2 +1`

<li>Quelle commande nous donne le nombre d’utilisateurs ?</li>

>`cat /etc/passwd | awk -F: '{print $ 1}'`
>`finger who w `

<li>Combien de pages de manuel comportent le mot-clé conversion dans leur description ?</li>
<li> A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine</li>

>`find -name passwd `

<li>Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier
~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null
</li>

>`echo  find -name passwd  >> ~/list_passwd_files.txt `

<li>Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu
précédemment
</li>

>`cd`
>`sudo grep `
<li>Utilisez la commande locate pour trouver le fichier history.log.</li>

>`~$ locate history.log `

<li>Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?</li>
*Non il n'apparait pas car il n'est pas dans l'arborescence*
*La commande locate permet de trouver très rapidement un fichier. Contrairement à ce que l’on pourrait penser locate ne vas pas chercher le fichier au sein de l’arborescence, mais au sein d’une base de données contenant la liste des fichiers existants.*
</ol>

