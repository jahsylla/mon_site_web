
# Config de l'ordi une fois par l'ordi
- git help 'nom commande' : permet d'avoir de l'aide sur une commande

# Configuration GIT
- git config --global user.email "jahsyllacamara@gmail.com" 
- git config --global user.name "jahsylla" : definir email et nom d'utilisateur 
- git config --list : voir la configuration définit
- git config --global code.editor nom de l'éditeur de texte


- git init : initialisation de git
- git status -s : etat d'un dossier 
- git add 'nom du fichier' : pour "STAGER" / INDEXER un/des fichier
- git restore --staged <fichier>
- git reset nom du fichier : pour désindexder un fichier
- git commit -m "un messge" : pour commiter/envoyé le fichier stager
- git commit -a -m "un messge" : pour faire le stage et le commit d'un coup
- git add "*.extension du fichier" : pour stager tous les fichier ayant cette extension car dans un projet on peut avoir plusieurs fichiers différents
- git add --all ou git add . : pour stager tous les fichiers dans le repertoire
touch .gitignore : creer un fichier pour mettre les " FICHIERS AVEC LEURS EXTENSIONS ou *.EXTENSIONS et aussi DES REPERTOIRE(e.g au format tmp/)" à ignorer si on mes un ! devant un fn dans le 
                   gitignore ce dernier ne sera pas ignorer malgrés les régle definit dans ce même fichier (alphorm git : video 7)
- git diff 'monfichier.ext" : pour voir la difference entre un monfichier qu'on est entrain d'editer et monfichier que j'avais deja commité, les choses supprimer aurons une coloration ROUGE et les choses ajouté une coloration VERTE.


# Historique d'un repo
L'historique d'un dépôt Git est constitué d'un ensemble de **commit** reliés entre eux par un pointeur.

un commit commit contien:
- SHAP-1 (id de 40 char)
- un ensemble de modification
- commentaire décrivant le commit
- Les informations sur l'auteur
- Une date de créaton
- Liste (SHAP-1) de son ou ses parents

- git log : historique/ des commit 
- git log -n 2 : e.g voir les deux derniers commit
- git log --oneline : affichage compresser en cas de plusieurs commit
- git log -p "monfichier.ext" : pour voir tous les commit concernant "monfichier"
- git shown id_commit : permet de voir les modif apporté lors d'un commit / le contenue d'un commit
- git checkout  num_SHAP-1_du_commit_d'interet 

# Les tags
Un tag c'est tout simplement un intitulé suivi d'un pointeur vers un comite.
Toutes les branches dans guide possèdent un tag à son nom.
Par exemple, notre branche Masters possède un tag qui s'appelle Master.
La particularité de ces tag reliés directement en branches, c'est qu'ils pointent directement sur le dernier comite de la branche donnée.

- Utiliser un tag plutôt qu'un SHAP-1 pour naviger sur l'historique
L'utilisation permet aussi d'indentifier des version de notre travail (ex: V1, V2, ...)
Pour ajouter un tag / poser un tag sur le commit courant on fait:
git checkout SHAP-1
git tag MON_SITE_V1 -m "la premiere version de mon site web"

git tag : affichier la liste de tag

Et pour revenir à la branche principale :
git checkout main
git checkout MON_SITE_V1 : pour revenir à la  v1 de mon site


`Alors, qu'est ce qu'un **pull request** ?`
Un pull request, c'est tout simplement une proposition de modification pour un dépôt dans lequel vous n'avez pas les accès.
Vous allez en fait dupliquer le projet (**fork**) en question puis faire des modifications dans le duplicate que vous avez fait de ce projet, puisque ce sera le vôtre dont vous aurez les droits d'accès. Et ensuite vous direz au développeur ou au propriétaire du dépôt principal: tenez, j'ai fait des modifications. La personne du repo OG va alors accepter ou Non les modifs pour les intégrer dans son propre repo. 

Est ce que vous voulez les prendre?
Et ensuite le propriétaire va pouvoir dire oui, je les prends ou non.

`Qu'est ce que un **ISSUE** ?`
C'est tout simplement un outil qui va permettre la gestion des anomalies. ou plus simplement de remonter des bug au developpeur

Donc, qu'est ce que c'est qu'une anomalie?
C'est tout simplement un bug par exemple.

Alors cette gestion d'anomalie, c'est une base de données qui va regrouper l'ensemble des bugs remontés par les utilisateurs ou des propositions d'évolution. Ensuite, les développeurs vont pouvoir trier et visionner ces propositions et ensuite soit corriger les bugs ou faire les évolutions proposées par les par les personnes qui utilisent l'outil.
Ça permet également d'avoir une sorte de messagerie d'échange entre les personnes qui testent par exemple le soft et les personnes qui développent celui ci.

si on font un commit pour un issue une bonne pratique est d'ajouter l'ID de l'issue dans le message du commit. Cela permet de faire un lien entre notre commit et la base des issues, ex:
- commit -m "#2: correction du code blablabla "

`Qu'est ce que un **gist** ?`
C'est tout simplement un outil qui va vous permettre de partager du code.
Cet outil est vraiment là pour partager des morceaux assez restreinte d'un code et pas tout un projet entier.
Ce partage va pouvoir se faire par exemple en insérant le gist sur un forum ou sur un site web ou encore en l'envoyant par mail.
Les personnes pourront alors consulter votre code et ajouter des commentaires à celui ci.


# Accéder à Github vi les Tokens
On peut accéder à github soit par:
- SSH : login/token
-HTTPS : login/mdp

git push -u origin main
- origin : le remote que l'on souhaite utiliser pour faire le push
- main : la branch que l'on veut pouser

git push -u origin MON_TAG : pour pousser un tag

git push origne --tags : pousser tous les tags

### Maitriser les modif
git blame mon_fichier : pour avoir des informations sur les modif d'un fichier 

### Sauvegarder temporairement / mettre de coté des modifications présent dans le work space
Supposons je suis entrain de développer une fonctionalité pour mon site depuis quelques heures. Ensuite j'ai envie de revenir à une version antérieur de mon site. Si je fait un `git checkout MON_TAG ou MON-SHAP-1` je risque de perdre mon travail sur la fonctionnalité que je suis entrain de développer pendant qq temps et git ne va pas être content et il ne va pas l'accepter.

Dans ce cas on peut utiliser git `git stash` pour garder dans un coin les modifications avec:
- git stash save " mon message " : pour save les modif non encore indexé
- git stash list : pour lister les stash
- git stash show index_du_stash : pour afficher les modif du stash

 A partir de maintenant je peut faire `git checkout MON_TAG ou MON-SHAP-1`. Et si j'ai finit je reviens sur la branch sur lequel j'étais entrain de dev la fonctionnalité avec `git checkout ma_branch`. Enfin pour restaure le sauvegarde de la modif fait avec la cmd `git stash save " mon message "` j'utilise la commande :
 - git stash pop  index_du_stash

 ### Faire un merge de fichier
 Comment fusionner deux version d'un même fichier ?

 supposons on travaille sur un fichier xxx.txt dans deux repos différents. Le user du repos un a déja finit son travail sur le fichier xxx.txt et la pousser sur le repos distant. Ensuite au moment de faire un pull git nous indique qu'il y un conflit, Dans ce cas il faut faire dans l'ordre suivant:
 - git stash
 - git pull
 - git  pull origin main
 - git stash pop : c'est ici que git va nou signaler les conflit qu'il faudra résoudre manuellement 
 - git status voir si par hasard tout est en ordre et qu'on a pas indexer par hasard d'autre fichier que l'on veut pas pousser
 
 A partir de la on peut ajouter et pousser nos modif en tout tranquillité

  ### Faire un merge de commit
  


ANNULER UN COMMIT:
- si on deja notre repos dand le clound et que l'on afait une erreur sur un fichier pour annuler un commit on doit d'abord corriger notre erreur ensuite refaire le commit du meme fichier concerné
- si on est en local (rien est encore dans le clound) on peut annuler le commit avec:
    - 1) git reset --hard id_commit_a_revenir : c-a-d on dit à git reviens à l'état que l'on avait avec le commit ayant pour id id_commit_a_revenir et annule tous les modif que j'ai eu aprés. Ensuite on pourra faire/continuer nos modif et ensuite l'ajouter à stagging area. Ensuite on fait :
        - git commit --amend : permet de dire que 'lon ne veut pas créer un nouveau commit mais juste ajouté la modif au précédent commit. si on ne veut pas modifié le message on use
        - git commit --amend --no-edit
    - 2) git reset --hard id_commit_a_revenir :  c-a-d il va revenir à l'état de id_commit_a_revenir mais il ne va pas annuler les modif fait 


                                                Comprendre Git (6/18) : Revenir en arrière

git checkout 'id du commit' : pour voir l'état du dépot au moment du commit précédent sans faire de modifications. NB : on ne peut qu(observé on ne peut rien modifier

.

git checkout 'id du commit' monfichier.ext : pour revenir en arriere du monfichier.ext lors de la dernier commit(etat = commit = id commit). Aprés modif on le stage et on le commit de facon classique.

git checkout master monfichier.ext : pour retourner en arriere dans monfichier.ext lors de la dernier commit.

git revert 'id du commit' : permet de défair un commit(défair ce qui a été fait aprés un moment donné mais ne le suppime pas car en faisant un nouvau git revert 'id du commit du revert précédent' on revient a l'état ou on été) NB : il ne permet pas de revenir en arriere.

git revert 'id du commit' monfichier.ext : permet de défaire les modifications qui ont été apporté a ce fichier   

git reset 'id du commit': revenir en arriere revenir a un commit précis  et supprime tout ce que l'on avait fait aprés ce commit. NB : faire TRES attention avec cette commande
git reset HEAD^ --mixed "monfichier.ext" : permet de sortir un fichier de la zone stagé (nb de ^ = nb de commit en arriere a retourner)
git reset -- hard "monfichier.ext" : revenir a la derniere commit de "monfichier.ext"



Supposons que l'on vient de faire un commit et on a oublié qq chose exemple un point virgule : on vas d'abord ajouter le point ";" a notre script en suite le stagé avec git add monfichier.ext ensuite utiliser la commande git commit --amend cela nous permet de conserver le meme 'message de commit" et ne pas bourré notre historique.


                                    J'ai fait mon commit un peu trop vite... est-ce que je peux l'annuler ?
                                    
git commit --amend -m "Votre nouveau message" : modifier le message du dernier commit
git revert SHADuCommit : créer un nouveau commit qui fait l'inverse du précédent
git reset --hard‌ SHADuCommit : retourner en arriere tous les changements que je n'ai pas encore commités




Travailler sur plusieurs branches est très utile lorsque vous souhaitez tester une expérimentation sur votre projet, ou encore pour vous concentrer sur le développement d'une fonctionnalité spécifique : 

git branch mabranche : creer une nouvelle branche
git checkout mabranche : pour se placer sur cette branche


Lorsque vous travaillez sur plusieurs branches, il va souvent vous arriver de vouloir ajouter  dans une branche A les mises à jour que vous avez faites dans une autre branche B. Pour cela, on se place dans la branche A :

- git checkout brancheA
Puis on utilise la commande git merge : 
git merge brancheB





                               DOCKER
https://towardsdatascience.com/build-a-docker-container-with-your-machine-learning-model-3cf906f5e07e
https://towardsdatascience.com/build-and-run-a-docker-container-for-your-machine-learning-model-60209c2d7a7f
https://mlinproduction.com/docker-for-ml-part-3/
https://theaisummer.com/docker/
https://towardsdatascience.com/docker-for-data-scientists-part-1-41b0725d4a50
https://towardsdatascience.com/getting-started-with-docker-for-data-scientists-a2ed505e2a09
https://dagshub.com/blog/setting-up-data-science-workspace-with-docker/
https://towardsdatascience.com/a-complete-guide-to-building-a-docker-image-serving-a-machine-learning-system-in-production-d8b5b0533bde




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

for branch in $(git branch -r | grep -v '\->'); do
  git checkout --track $branch
done