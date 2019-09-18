#  Administration Système TP 2 - Bash

<ol>
<li>Dans quels dossiers bash trouve-t-il les commandes tapées par l’utilisateur ?</li>

*dans les dossiers contenues dans le path*

 >`printv PATH`

*user/local/sbin*

<li>Quelle variable d’environnement permet à la commande cd tapée sans argument de vous ramener dans
votre répertoire personnel ?
</li>

*varibale d'environnement HOME conteneur et $HOME est contenue de la variable home*

 >`printenv HOME`

<li>. Explicitez le rôle des variables LANG, PWD, OLDPWD, SHELL et _.
</li>

 >`printenv LANG`

*définie et modifie  le language et les caractères informatique utilisé*

>`printenv PWD`

*définie le chemins du dossier personnel*

>`printenv OLDPWD`

*ancien chemin du dossier personnel*

>`printenv SHELL`

*indique l'intéprèteur shell utiliser (son chemin)*

>`printenv _`

*dernieère commande utiliser par l'utilisateur*

<li>Créez une variable locale MY_VAR (le contenu n’a pas d’importance). Vérifiez que la variable existe.
</li>

>`message='bonjour'`
>`echo $message`

<li>Tapez ensuite la commande bash. Que fait-elle ? La variable MY_VAR existe-t-elle ? Expliquez. A la fin
de cette question, tapez la commande exit pour revenir dans votre session initiale.</li>

*non elle n'existe plus car on a ouvert un nouvelle shell et on doit exit pour retourner a l'ancienne*

>`bash`
>`ouverture d'un nouveau shell invite de commande`


<li>Transformez MY_VAR en une variable d’environnement et recommencez la question précédente. Explique
</li>

>`export message`

*maintenant le contenue de la variable est disponible dans tout les shells*

<li>Créer la variable d’environnement NOMS ayant pour contenu vos noms de binômes séparés par un espace.
Afficher la valeur de NOMS pour vérifier que l’affectation est correcte</li>

>`export NOMS = "chavee abitbol"`
>`printenv NOMS`
<li>
Ecrivez une commande qui affiche ”Bonjour à vous deux, binôme1 binôme2 !” (où binôme1 et binôme2
sont vos deux noms) en utilisant la variable NOMS.
</li>

>`echo Bonjour à vous deux $NOMS`

<li>. Quelle différence y a-t-il entre donner une valeur vide à une variable et l’utilisation de la commande
unset ?
</li>

*unset détruit la variable créer et l'autre la variable existe mais sans rien dedans*

<li>
Utilisez la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre
dossier personnel d’après bash)
</li>

>`echo '$HOME'="$HOME"`

</ol>
<h1>Programmation Bash
</h1>
<ol>
<li>
Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au
contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par
l’utilisateur ne doit pas s’afficher.
</li>

### Exercice 2. Contrôle de mot de passe 

Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par l’utilisateur ne doit pas s’afficher.


 création du fichier :

>`touch testpwd.sh`

script exécutable  :

>`chmod u+x testpwd.sh`


contrôleur de mot de passe :
<pre>
#!/bin/bash                             
PASSWORD="test"
echo "Veuillez saisir votre mot de passe"
read -s mdp
if [ $mdp = $ PASSWORD ]; then
    echo "Mot de passse correcte"
else
    echo "Mot de passe incorrecte"
fi
</pre>
test du script :
>`./testpwd.sh`

### Exercice 3. Expressions rationnelles 

Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre est un nombre réel.

création du fichier  de l'exo 3:

>`touch exo3.sh`

création d'un script éxecutable:

>`chmod u+x exo3.sh`

>`nano exo3.sh`

test du contrôle d'utilisateur:
<pre>
#!/bin/bash
function is_number()
{
    re='^[+-]?[0-9]+([.][0-9]+)?$'
    if ! [[ $1 =~ $re ]]; then
        return 1
    else
        return 0
    fi
}
is_number $1
if [ "$?" = "0" ]; then
    echo "C'est un nombre réel"
else
    echo "Ce n'est pas un nombre réel"
fi
</pre>
lancement du script avec paramètre:
>`./exo3.sh *parametre*`

### Exercice 4. Contrôle d’utilisateur

Écrivez un script qui vérifie l’existence d’unutilisateur dont le nom est donné en paramètre du script. Si le script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation:nom_du_scriptnom_utilisateur”, où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre script, le message doit changer automatiquement)

 création du fichier :

>`touch control_user.sh`

 script exécutable  :

>`chmod u+x control_user.sh`


>`nano control_user.sh`

test du  contrôle d'utilisateur:
<pre>
#!/bin/bash
new_user=$1
id -u "$new_user"> /dev/nul 2>&1
if [ "$?" = "0" ]; then
    echo "Utilisateur valide"
elif [ -z "$new_user" ]; then
    echo "Utilisation : $0 nom_utilisateur"
else
    echo "Utilisateur invalide"
fi
</pre>

éxécution du script  :
>`./control_user.sh *parametre*`

Le script prend un paramètre est le test pour voir si il affiche différent resultat en fonction du paramètre. 

### Exercice 5. Factorielle 

Écrivez un programme qui calcule la factorielle d’un entier naturel passé en paramètre (on supposera que l’utilisateur saisit toujours un entier naturel).

création du fichier :

>`touch facto.sh`

 script exécutable  :

>`chmod u+x facto.sh`


>`nano facto.sh`

test pour le contrôle d'utilisateur:
<pre>
#!/bin/bash
fact()
{
    n=$1
    if [ $n = 0 ]; then
        echo 1
    else 
        echo $(( n * `fact $( n - 1 ))` ))
    fi
}
echo `fact $1`
</pre>

Avec la ligne de commande suivante je peux lancer le script :
>`./facto.sh *parametre*`

passage du paramètre dans la fonction.

### Exercice 6. Le juste prix

Écrivez un script qui génère un nombre aléatoire entre 1 et 1000 et demande à l’utilisateur de le deviner. Le programme écrira ”C’est plus!”, ”C’est moins!” ou ”Gagné!” selon les cas (vous utiliserez $RANDOM).


 création du fichier :

>`touch juste_prix.sh`

script exécutable :

>`chmod u+x juste_prix.sh`

>`nano juste_prix.sh`

test du  le contrôle d'utilisateur:
<pre>
#!/bin/bash

echelle=1000
randomnumber=$RAMDOM

let "randomnumber %= $echelle"

echo "Veuillez saisir un nombre aléatoire entre 1 et 1000"
read number

while [ $number -ne $randomnumber ]
do
    if [ $number -lt $randomnumber ]; then
        echo "C'est plus !"
    elif [$number -gt $randomnumber ]; then
        echo "C'est moins !"
    fi

echo "Veuillez saisir un aujtre nombre"
read newnumber
number=$newnumber

done

if [ $number -eq $randomnumber ]; then
    echo "C'est gagné !"
fi
</pre>

éxecution du script :
>`./juste-prix.sh`


</ol>
