# TD 1
## Remarques préliminaires
* Pour l'ensemble des TDs, vous créerez un compte individuel sur [github](https://github.com/).
Vous nommerez ce compte de la façon suivante: `uvsq<MonNuméroÉtudiant>`.
Par exemple, pour un étudiant de numéro *21601234*, le compte sera `uvsq21601234`.
* Les commandes `git` sont à taper en ligne de commande dans un *shell*.
* Vous pouvez utiliser l'IDE de votre choix.
Sur le cartable numérique, [Eclipse](www.eclipse.org), [IntelliJ IDEA](http://www.jetbrains.com/idea/) et [Visual Studio Code](https://code.visualstudio.com/) sont installés.
* Vous répondrez aux questions directement dans ce fichier en complétant les emplacements correspondants
* Vous déposerez une archive contenant l'ensemble de votre travail sur Moodle.

## Partie en présentiel : découverte de `git`
Dans cet exercice, vous créerez une classe `Fraction` représentant un nombre rationnel et une classe `Main` qui testera les méthodes de la classe `Fraction` **avec des assertions**.
À chaque étape, consultez le statut des fichiers du projet ainsi que l'historique.

1. Sur la forge, créez le projet Java `SimpleFraction`;
En terme de *commits*, quelle différence constatez-vous entre cocher une (ou plusieurs) des cases *Initialize this repository with* et n'en cocher aucune ?
    > Cocher une ou plusieurs cases permettra de créer un commit d'initialisation, alors que si on en coche aucune, ce premier commit ne sera pas crée.

    Pour la suite, ne cochez aucune de ces cases.
1. Localement, configurez `git` avec votre nom (`user.name`) et votre email (`user.email`);
    ```bash
    $ git config --global user.name "Mattéo Giraudo"
    $ git config --global user.email matteo.giraudo@ens.uvsq.fr
    ```
1. Initialisez le dépôt `git` local pour le projet;
    ```bash
    $ git add
    $ git remote add origin https://github.com/uvsq21806570/SimpleFraction
    
    Option Alternative :
    $ git clone https://github.com/uvsq21806570/SimpleFraction
    ```
1. Créez la classe `Fraction` (vide pour le moment) et la classe `Main` (avec un simple affichage) dans le projet;
Vérifiez que le projet compile et s'exécute dans l'IDE;
Validez les changements;
    ```bash
    Compilation : $ javac Fraction.java Main.java
    Execution : $ java -ea Main
    Validation des changements :
    $ git add Fraction.java Main.java
    $ git commit -m "Classes Fraction (vide) et Main (Avec un affichage simple : Hello World !)"
    Il est conseillé ici donc de faire les 2 lignes de commandes suivantes :
    $ git status
    $ git log
    ```
1. Ajoutez un constructeur et la méthode `toString` à la classe `Fraction` et modifiez la classe `Main` en conséquence;
Validez les changements;
    ```Java
    Fraction f = new Fraction (3,2);
    assert f.toString() == "3/2";
    Commandes pour valider les changements :
    $ git status
    $ git add Fraction.java Main.java

    ```
1. Publiez vos modifications sur le dépôt distant;
Vous utiliserez le protocole `https` pour cela;
Vérifiez avec le navigateur;
    ```bash
    La commande suivante a été réalisé lors de l'initialisation du git :
    $ git remote add origin https://github.com/uvsq21806570/SimpleFraction

    Publication des modifications :
    $ git push -u origin master
    ```
1. Sur la forge, ajoutez un fichier de documentation `README.md`.
Quelle syntaxe est utilisée pour ce fichier ?
    Le fichier README.md se finit par md.
    Ainsi, on peut en déduire que la syntaxe est le markdown.
1. Récupérez localement les modifications effectuées sur la forge.
    ```bash
    $ git pull : Cela va nous permettre de récupérer le README.md (crée sur github) sur notre IDE.
    ```
1. Ajoutez les répertoires et fichiers issus de la compilation aux fichiers ignorés par `git` (fichier `.gitignore`);
    ```bash
    $ touch .gitignore
    .gitignore : *.class
    fichiers présents dans .gitignore : Fraction.class et Main.class
    ```
1. Retirez les fichiers de configuration de l'IDE du projet;
    ```bash
    Aucun retrait de fichier de configuration fut nécessaire.
    ```
    Ajoutez-les aux fichiers ignorés par `git`.
    ```bash
    Aucun ajout de fichier de configuration est donc nécessaire.
    ```
1. Configurez l'accès par clé publique/clé privée à la forge (cf. [Use the SSH protocol with Bitbucket Cloud](https://confluence.atlassian.com/bitbucket/use-the-ssh-protocol-with-bitbucket-cloud-221449711.html)).
    Question réalisée sous Linux.
    Nous avons tout d'abord crée une identité et une clé SSH (composée d'une clé privée et clé publique), suivi d'un mot de passe pour l'accès à cette clé.
    Ensuite, on rajoute notre clé sur l'agent ssh, cela nour permettra de pas écrire notre mot de passe pour pouvoir communiquer entre la forge et notre IDE.
    L'étape suivante est d'ajouter la clé publique sur le compte de notre forge en question, ici c'est GitHub.
    De ce fait, on ouvre à l'aide du terminal le fichier .pub, qui contient la clé publique. On la transfère à l'aide d'un copier-coller sur GitHub.
    Cela permet donc de ne plus à avoir besoin d'utiliser son mot de passe pour communiquer entre GitHub et sa machine personnelle, car ces 2 éléments utiliseront la clé SSH pour se connecter, se reconnaître et donc communiquer.


## Partie en distanciel : révisions et perfectionnement *shell* et *IDE*
### Maîtriser le *shell* de commandes
L'objectif de cet exercice est de vous faire réviser/découvrir les commandes de base du *shell* de votre machine.
Vous pouvez répondre en utilisant le shell de votre choix (*bash*, *Powershell*, ...).
Pour répondre à ces questions, vous devez effectuer les recherches documentaires adéquates (livre, web, ...).

1. Quel OS et quel shell de commande utilisez-vous ?
    L'OS utilisé est Linux Debian.
    Le shell de commande utilisé est bash.
1. Quelle commande permet d'obtenir de l'aide ?
Donnez un exemple.
    ```bash
    Une commande permettant d'obtenir de l'aide est "man".
    Exemple : $ man bash
    ```
1. Donnez la ou les commandes shell permettant de
    1. afficher les fichiers d'un répertoire triés par taille (taille affichée lisiblement)
        ```bash
        $ ls -lSh.
        ```
    1. compter le nombre de ligne d'un fichier
        ```bash
        $ wc -l
        ```
    1. afficher les lignes du fichier `Main.java` contenant la chaîne `uneVariable`
        ```bash
        $ grep "uneVariable" Main.java
        ```
    1. afficher récursivement les fichiers `.java` contenant la chaîne `uneVariable`
        ```bash
        $ grep -r --include "*.java" "uneVariable"
        ```
    1. trouver les fichiers (pas les répertoires) nommés `README.md` dans une arborescence de répertoires
        ```bash
        $ find . -type f -name "README.md"
        ```
    1. afficher les différences entre deux fichiers textes
        ```bash
        diff <fichier_1> <fichier_2>
        ```
1. Expliquez en une ou deux phrases le rôle de ces commandes et dans quel contexte elles peuvent être utiles pour un développeur.
    * `ssh`
        ssh est un programme utilisé pour accéder à des fichiers/répertoires sur un serveur distant et permet des communications encryptées et sécurisées entre 2 hôtes, généralement la machine locale et la machine distante.
        C'est donc une commande très utile pour transférer des fichiers à l'aide du terminal/en ligne de commande.
    * `screen`/`tmux`
        Screen est une commande permettant d'ouvrir plusieurs terminaux sur une même console. Cela peut permettre d'aider un utilisateur distant en partageant un terminal avec lui.
        D'un autre côté, tmux est une commande permettant d'utiliser plusieurs terminaux sous un unique affichage. On peut utiliser cette commande pour avoir un terminal qui affiche l'heure et un autre qui permet de programmer, compiler et exécuter des programmes.
    * `curl`/[HTTPie](https://httpie.org/)
        HTTPie est une commande permettant de debogger mais aussi d'intéragir avec des interfaces utilisateur ou encore des serveurs HTTP. Le développeur peut l'utiliser pour télécharger des fichiers/images ou encore entrer des requêtes HTTP tout en étant hors-ligne.
        De même, curl est une commande qui permettra de télécharger des ressources et fichiers disponibles sur le réseau, mais aussi de les envoyer. Le protocole réseau principal est HTTP.
        Le développeur l'utilisera surtout pour sa fonction de téléchargement et d'information concernant les balises ou encore les éventuels cookies.
    * [jq](https://stedolan.github.io/jq/)
        jq correspond à une commande de type filtre. En effet, elle permet de filtrer, découper et regrouper des données de manière à ce qu'un développeur puisse créer des tubes (pipes). On utilisera souvent cette commande pour extraire des données puis les transformer de manière à les réorganiser.

### Découverte de votre *IDE*
Dans cet exercice, vous expliquerez en quelques phrases comment vous réalisez les actions ci-dessous dans votre IDE.
Vous pouvez choisir l'IDE/éditeur de texte de votre choix.
Pour réaliser cette exercice, vous devez bien évidemment vous reporter à la documentations de l'IDE ([IntelliJ IDEA](https://www.jetbrains.com/help/idea/discover-intellij-idea.html#developer-tools), [Visual Studio Code](https://code.visualstudio.com/docs), [Eclipse](https://help.eclipse.org/2020-09/index.jsp), ...).

1. Quels IDE ou éditeurs de texte utilisez-vous pour le développement Java ?
    Eclipse et Visual Studio Code. On utilise Eclipse pour la partie "Découverte de votre IDE".

    Pour la suite, ne considérez que l'un de vos choix.
1. Comment vérifier/définir que l'encodage utilisé est *UTF-8* ?
    On sélectionne un fichier, on regarde ses propriétés puis on regarde en fin de page, l'encodage utilisé est spécifié et modifiable.

1. Comment choisir le JDK à utiliser dans un projet ?
    On sélectionne notre projet, on regarde ses propriétés, puis on sélectionne les éléments suivants :
    Java Build Path -> Libraries -> JRE System Library -> Edit.
    Puis on peut modifie l'environnement d'exécution et choisir le JDK que l'on souhaite utiliser.

1. Comment préciser la version Java des sources dans un projet ?
    On sélectionne notre projet, on regarde ses propriétés, on sélectionne Java Compiler puis on peut changer la version Java à l'aide de l'option "Source compatibility".

1. Comment ajouter une bibliothèque externe dans un projet ?
    On sélectionne notre projet, on regarde ses propriétés, puis on sélectionne les éléments suivants :
    Java Build Path -> Libraries.
    Puis on peut utiliser l'option "Add External JARs..."

1. Comment reformater un fichier source Java ?
    On sélectionne notre fichier.java puis les éléments suivants :
    Source -> Format. S'il ne se passe rien, cela signifie que notre fichier Java est déjà formaté.

1. Comment trouver la déclaration d'une variable ou méthode ?
    On sélectionne une variable/méthode dans notre programme, on effectue un clique droit dessus, puis on utilise l'option "Open Declaration". Cela va nous montrer la déclaration de la variable choisie.

1. Comment insérer un bloc de code prédéfini (*snippet*) ?
    On effectue le raccourci ctrl + espace à la suite d'un début de code ou d'un terme. Par exemple, on peut écrire dans un programme : "for" puis effectuer un ctrl+espace, ce qui va nous permettre d'insérer (entre plusieurs) un type de for.

1. Comment renommer une classe dans l'ensemble du projet ?
    On sélectionne notre classe, puis on effectue les éléments suivants : Refactor -> Rename.
    On peut ainsi renommer sa classe.

1. Comment exécuter le programme en lui passant un paramètre en ligne de commande ?
    En haut de l'onglet, on sélectionne : Run -> Run Configurations -> Arguments.
    On peut ainsi passer un paramètre en ligne de commande.

1. Comment déboguer le programme en visualisant le contenu d'une ou plusieurs variables ?
    En haut de l'onglet, on sélectionne : Run -> Debug.
    De plus, on peut au préalable double cliquer à la gauche du numéro d'une ligne de code, ce qui permet de générer un breakpoint à l'endroit où l'on souhaite visualiser les variables.
    
1. Quels paramètres ou fonctionnalités vous semblent particulièrement importants/utiles pour le développement Java ?
    Deux fonctionnalités me semblent utiles et agréables pour un individu qui étudie le développement Java : Tout d'abord, la possibilité de retrouver les déclarations de variables et méthodes en quelques clics réduit les chances de s'embrouiller dans de longs programmes, puis les insertions de blocs de code prédéfini permettent une programmation plus fluide.