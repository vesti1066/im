# Animation - révision

## Mise en place

Un des "hello world" de l'animation est celui de la balle qui rebondit sur les bords de l'écran. Nous allons ici réalisez la chose en ajoutant une simulation de la gravité et du frottement. Nous pourrions reprendre les équations physiques pour ce mouvement,  mais nous allons plutôt utiliser des simplifications permettant toutefois d'obtenir un bon résultat.

## Rebondir sur les bords du *canvas*
Créez un nouveau fichier nommé *Bouncing.js* dans *class/Circle/* et codez une classe héritant de la classe *Circle*.  Dans cette nouvelle classe, nous allons développer un peu la classe de base en remplaçant la vitesse par deux *vélocités*, une pour les X et une pour les Y (ce qui formera notre vecteur de vitesse). De plus le constructeur devra aussi recevoir les bornes supérieures (largeur et hauteur) du *canvas* afin de correctement rebondir sur ces limites. Créez donc le constructeur adéquat pour prendre en compte ces modifications.

### Méthode *move*
Contrairement à la méthode *move* de la classe parente, la nouvelle ne doit plus prendre d'angle en paramètre (puisque l'on a déjà un vecteur de vitesse). Surcharger donc la méthode *move* pour calculer les (x,y) du cercle en prenant en compte les deux vélocités X et Y. N'oubliez pas de multiplier par Δt. 

### Boucle d'animation

Dans votre programme principal, testez votre nouvelle classe en créant un cercle. Puis créez une *boucle* d'animation (grâce à *requestAnimationFrame*) , calculez le Δt, faites bouger votre cercle et redessinez le *canvas*. 

### Méthode *bounceOffTheWalls*

Rajoutez une méthode *bounceOffTheWalls* dans votre classe. Lorsque le cercle touche (ou déborde) des bords du *canvas*, inversez la vélocité associée.  Appelez cette nouvelle méthode dans votre boucle d'animation juste après le mouvement de votre cercle pour la tester.

### Méthode *applyGravity*: simulation de la gravité et de l'élasticité (coefficient de restitution)

Rajoutez une méthode *applyGravity* dans votre classe. Cette méthode recevra le Δt et une gravité et modifiera la vélocité Y en conséquence. Appelez cette nouvelle méthode dans votre boucle d'animation juste après le mouvement de votre cercle pour la tester. Si vous n'avez pas repris les équations de physique pour la gravité, vous vous apercevrez que votre balle n'aura pas un mouvement très naturel.  Pour l'améliorer (tout en restant dans la simplification des équations de physique), nous pourrions rajouter un coefficient de restitution (élasticité) lors du rebond sur le bord bas du *canvas*. Pour le faire, modifiez la méthode *bounceOffTheWalls* pour y ajouter un paramètre *withGravity* de type booléen. Modifiez ensuite le code du rebond sur le bas du *canvas* pour que celui ci applique une réduction de la vélocité Y.  Testez quelques idées afin d'obtenir un mouvement suffisamment réaliste dans votre animation.

### Méthode *applyFriction* : simulation du frottement de l'air et du sol
Rajoutez une méthode *applyFriction* dans votre classe. Cette méthode recevra en paramètre le Δt ainsi qu'une valeur de simulation pour le frottement. Son code modifiera les vélocités X et Y en conséquence. Appelez cette nouvelle méthode dans votre boucle d'animation juste après le mouvement de votre cercle pour la tester. Comme vous le constaterez, votre balle roulera un peu trop longtemps sur le *sol*.  Ajoutez donc une nouvelle méthode *applyFloorFriction* dans votre classe, celle-ci recevra aussi le Δt ainsi qu'une valeur de simulation pour le frottement au sol. Elle appellera votre méthode *applyFriction* avec ces paramètres  uniquement si le cercle est en contacte avec le sol. Testez à nouveau votre animation et ajustez les paramètres de friction pour que le mouvement vous paraisse adéquat.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzgyNzQ0Nl19
-->