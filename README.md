# GEO7630
![](https://lh7-us.googleusercontent.com/xXpwCLySEdBjTJXbrnWDmOb1Cu4IO2V5FDDSVnd-8YPCiWZpn5dweBmT0QSpubJ4ae1xjJjOyb9OGrbXkUcSIv-1jWBTPqOI9mXgtAYaEPrCA0bMM8z36MZdw-hRKb3T9O06ElZp0HcRWSHCigJS8VI)

Le fichier de réseau cyclable est coupé en tronçon d’une longueur maximale de 75m. On rajoute ensuite des valeurs d’indice de qualité d’usage en fonction des champs qui nous intéressent. On extrait ensuite les coordonnées de debut et de fin de chaque segment. On crée finalement un fichier de points pour l’extrémité de début et un autre fichier pour l’extrémité de fin, sur lesquels on viendra apposer les élévations des rasters afin de calculer les pentes. 

![](https://lh7-us.googleusercontent.com/dR9w9sG7i7d66y-j--wMisSrVhR8WfVkq2pT1D7pTPrHJDwvVrDrlSx2Axzs0E828VhaT2wWThRm3J3bwUUY-RcmDxG0FDF4aFvq52uEVZEtMfI2bJjyamYgakFCmnAL4wOiQZcRhV5TXpso3Jqn_o4)

On produit ici un indice de pente. Les pentes les plus faibles ont un meilleur indice de qualité d’usage. On calcule les pentes à partir de la différence d’élévation au début et à la fin de chaque tronçon, ainsi que de sa longueur. 

![](https://lh7-us.googleusercontent.com/mO2vnBM2PZUcDdr5mYU2UMfkWwguKrrxGBxDECDnzGokDbaJTQOhOdsVNNpF77s8-dpGRno4U1JmDRzm7NYf_12EAVY5AoNu3dykgBkGMCcieZ02eVt1jTyqqMRtsk10i3rUWwL-sacbyT44fyIojS4)

Ici, on ajoute un indice de qualité des pistes cyclables en fonction de la zone d’îlot de chaleur de la piste cyclable. 

![](https://lh7-us.googleusercontent.com/Eo3fWQBp-Q2vpnNb-JvBsQti8obgPrq5v6L3BnuF5CzAt6_rXtCOgBr8WohaNvqQzuvyliKZaRuoYMg904Xb8fjBF2SJAIT61QX5gx_TbhAPKc3EzrhmHhGdHXyCn1gJYcRCo7M3RH79Jvd8ptu9cPM)

On ajoute un indice de qualité des pistes cyclables en fonction de la distance d’un espace vert. En utilisant une combinaison de plusieurs buffers et de clips, on arrive à avoir un résulat similaire au multiple ring buffer d’arcgis. On appose ensuite un indice en fonction de la zone de buffer de la piste cyclable. 

![](https://lh7-us.googleusercontent.com/Hhx6AKiMOtiKL1ftmiUXC9LkUOD88DI3ppy3ZTkUxmftW1Rou0ZKIDYlFTBrH-4Wj-CxuySNrJtHgPa1JF5oUzfOX65P_DBRlsY4DYG640gaFxmTV7rYtRKLQf8oue8X4m1y_4zm017TQCSUzGilDUI)

Pour le réseau routier, on utilise la même technique des multiple ring buffer que pour les espaces verts et on ajoute les indices aux pistes cyclables. 

![](https://lh7-us.googleusercontent.com/n1plJHS6SQJA8C3W14nYTF0ZMeyzVb5aH3vDSlxbI1RTS9KZm4r-p6ABXihQkzGQxE7CU1vXsHApYIzZmCALyaGg7gWHNqG676NLCsgOgWSaKrpP4V-CBd9JZZBqXj0-mYA54z_KhuIo5ywKCqFbMmI)

Pour les travaux, on joint les 2 fichiers contenant l’ensembles des informations nécessaires. On va ensuite premièrement calculer un indice vis à vis les obstructions de pistes. On utilise un petit buffer pour venir joindre topologiquement les lignes des pistes aux points des travaux. Deuxièmement, on crée un indice d’inconfort lié aux travaux et on appose l’indice aux pistes avec la technique du buffer expliqué dans le “premièrement”.

![](https://lh7-us.googleusercontent.com/JSDGrp696Xe3isHYDtdc1N4spCu7VlTNZc_P7eZeZhNf_WJaiCsYeEiVu-bgHBHtoe7Gb3F_Asv_Xe9cfyCG3hNS3ZuLxCDJCxp5JrEi0mePvbL9UB5poj5D0d9HhBuD0zGviBbGUSK5OlDvCB620gA)

Pour les collisions routières, on ajoute 3 indices en série en fonction de 3 champs, qu’on appose ensuite aux pistes cyclables avec le neighbor finder.

![](https://lh7-us.googleusercontent.com/7gfZNDzqeREANz0a9qjs-Le1T5Jehb_IOFmXUbf2259sKy_AMuOlj8-0UxL8DKFvJJ9iiAaEb6sBst4oLxZE6tNvTsG_LZbVR3L0mA_KaACVfy3z8TA5icdF-Wtw1lM5PoLsihwU8gCw4puyx2_0WO8)

Ce bookmark calcule l’indice final pour chaque piste cyclable. Chaque piste cyclable est définie par l’ensemble des tronçons continus sur une même route. Ensuite pour les pistes sans champ de rue, on a utilisé les noms de parcs, lesquels il a fallu concaténer les bonnes parties de texte. Ensuite, on calcule le nombre de tronçons de rue par parc afin de normaliser par ratio la somme des indices des tronçons.

![](https://lh7-us.googleusercontent.com/bM9OyMyhvwvuHR-kc3U7f_1paVni8w4SH3tN_MXtB129fyf72GLegOAvf1Dk1X7EkumXSaDAX4X82MaiwmLSPKY8hh030yCjxcHDN8mhpw4jgaMRRqUmlr1-ikyM54Lvx22y1XR25ftzSv53_dGnL30)

Finalement, ce bookmark sert à l’importation finale des données dans le serveur postgres. Le change detector permet de mettre à jour les données des travaux qui changent souvent. Comme les dates des travaux sont stockés dans la BD, il sera possible de visualiser l’historique des travaux. Les éléments sont finalement écrits dans la BD afin de visualiser les résultats. 
