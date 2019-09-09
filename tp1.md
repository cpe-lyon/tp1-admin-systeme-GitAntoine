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

   >`#cd `

<li>. revenez au dossier précédent (/var)</li>

   >`#cd -`


<li>essayez d’accéder au dossier /root; que se passe-t-il?</li>

*je n'est pas la permission*

<li>essayez la commande sudo cd /root; que se passe-t-il? Expliquez</li>

*commande n' éxiste pas car cd n'est pas un programme mais une commande intégrer(sudo ne s'applique qu'au programme)*

<li> à partir de votre dossier personnel, créez l’arborescence suivante </li>

 >`#sudo mkdir dossier1`
 >`#sudo mkdir dossier2`
 >`#cd dossier2`
 >`#sudo mkdir dossier2.1`
 >`#sudo mkdir dossier2.2`
 >`#sudo mkdir dossier1/dossier2`

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
</ol>

