# FCSC 2021 File Format

Lorsqu’un signal radio est représenté numériquement, il est composé d’une suite d’échantillons. L’une des méthodes d’échantillonnage très utilisée est l’échantillonnage I/Q, où chaque échantillon est représenté par une composante I (composante de phase) et une composante Q (composante de quadrature). L’une des représentations numérique d’un signal I/Q supportée par les principaux outils de traitement du signal est d’avoir une succession d’échantillons, avec chaque composante I et Q de chaque échantillon représentée par un nombre flottant compris entre 0 et 1, sur 32 bits, en mode petit-boutiste. Le schéma ci-dessous montre ce format :

```
+-------+-------+-------+-------+-------+-------+     +-------+-------+
|  i_0  |  q_0  |  i_1  |  q_1  |  i_2  |  q_2  | ... |  i_n  |  q_n  |
| (f32) | (f32) | (f32) | (f32) | (f32) | (f32) | ... | (f32) | (f32) |
+-------+-------+-------+-------+-------+-------+     +-------+-------+
```
Le fichier file-format.iq contient un signal représenté sous la forme décrite plus haut. Vous devez séparer les composantes I et Q et calculer le hash SHA256 résultant :

```
hash = SHA256(i_0 || i_1 || ... || i_n || q_0 || q_1 || ... || q_n)
flag = FCSC{<hash en minuscules>}
```


Notes :
- Note 1 : || dénote la concaténation, exemple : i_0 || q_0 = 20cebb3e || df342a3f = 20cebb3edf342a3f.
- Note 2 : pour résoudre ce challenge, il faut bouger des octets et aucun décodage de nombre flottant n’est nécessaire.


Fichier : 
- [file-format.iq](file-format.iq)



Auteur : ElyKar

Origine : [File Format](https://hackropole.fr/fr/challenges/hardware/fcsc2021-hardware-file-format/)



-----------

## Installation manuel
Vous n'utilisez pas l'application **les CTFs de Cyrhades** ? C'est dommage !
Mais voici comment installer ce CTF manuellement :

> git clone https://github.com/Hack-Oeil/fcsc2021-hardware-file-format.git

> cd fcsc2021-hardware-file-format


-----------

## Sur le site officiel hackropole.fr
> https://hackropole.fr/fr/challenges/hardware/fcsc2021-hardware-file-format/