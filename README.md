# Technical test

## Introduction

Fabien just came back from a meeting with an incubator and told them we have a platform “up and running” to monitor people's activities and control the budget for their startups !

All others developers are busy and we need you to deliver the app for tomorrow.
Some bugs are left and we need you to fix those. Don't spend to much time on it.

We need you to follow these steps to understand the app and to fix the bug : 
 - Sign up to the app
 - Create at least 2 others users on people page ( not with signup ) 
 - Edit these profiles and add aditional information 
 - Create a project
 - Input some information about the project
 - Input some activities to track your work in the good project
  
Then, see what happens in the app and fix the bug you found doing that.

## Then
Time to be creative, and efficient. Do what you think would be the best for your product under a short period.

### The goal is to fix at least 3 bugs and implement 1 quick win feature than could help us sell the platform

## Setup api

- cd api
- Run `npm i`
- Run `npm run dev`

## Setup app

- cd app
- Run `npm i`
- Run `npm run dev`

## Finally

Send us the project and answer to those simple questions : 
- What bugs did you find ? How did you solve these and why ? 
- Which feature did you develop and why ? 
- Do you have any feedback about the code / architecture of the project and what was the difficulty you encountered while doing it ? 

Bugs Fixés :

1) Lorsque l'on voulait modifié un profil, il était impossible de modifié le champ "Name". Je me suis apperçu que ce champ avait l'attribu "disabled", je l'ai donc mis en commentaire. (/app/src/scenes/user/view.js ligne 63)

2) Toujours lorsque l'on voulait modifié un profil, lorque l'on cliquait sur le bouton "Update", rien ne se passait. J'ai donc modifié l'évènement "onChange" en "onClick". (/app/src/scenes/user/view.js ligne 135)

3) Lorsque l'on créait un profil, le champ "Name" ne s'enregistrait pas. J'ai donc changé le nom de l'input en "name" et le la valeur en "user.name" comme cela est défini dans le state "values". (/app/src/scenes/user/list.js ligne 131)

4) Lorsque l'on cliquait sur un projet que l'on venait de créer, une erreur apparaissait. Je ne comprenais pas d'où venait cette erreur, alors j'ai essayé de mettre des "console.log" pour comprendre quel morceau de code était impliqué. Et j'ai fini par trouver que cela posait problème au niveau du backend. Je me suis aussi apperçu que lorsque l'on cliquait sur un projet, c'était un tableau qui était retourné, j'en ai déduit que l'affichage n'arrivait pas à ce faire avec un tableau. Après avoir cherché sur internet, j'ai trouvé que la commande find retournait un tableau avec tous les éléments correspondants. J'ai donc remplacé cette commande par findOne qui lui retourne le premier élément uniquement. (/api/src/controllers/project.js ligne 22)

Implémentation :

J'ai implémenté 2 petites features, tout d'abord, lors de la modification d'un profil, j'ai changé l'input de texte du champ "Job title" en une balise select. Ainsi cela évite les erreurs dans la gestion des postes des profils. (/app/src/scenes/user/view.js lignes 83-92)

Ensuite, j'ai rajouté un bouton "Signaler un bug" en bas à gauche de la page. Lorsque l'utilisateur clique sur ce lien, cela permet d'envoyer un mail à l'administrateur. Ainsi, cela permet de fluidifier et d'accélérer les démarche lorsqu'un bug se produit. (/app/components/header/drawer.js ligne 22)