                     Intoduction


L'entrprise bosh-cyber leak  a été compromise, et que l'attaquant aurait exfiltré des outils secrets très dangereux,l'administration a mis le site sous maintenance et j'ai été recruté en tant qu'investigateur afin de decouvrir ce que l'attaquant a exfiltré. L'objectif est de faire une analyse forensique du système afin d'identifier les différentes failles et les éléments utilisées par l'attaquant


                     Methodologie

- Analyse des traces sytèmes

/var/log: répertoire contenant l'arborescence de toutes les traces systèmes et applicatives. C'est dans ce répertoire qu'il est possible de consulter les traces des historiques de démarrage du système, de connexion des comptes utilisateurs, d'activité des services réseaux (SSH, HTTPD, SMTP, etc.) ainsi que les traces du noyau.

#cd /var/log
#ls
les éléments analysées dans /var/log sont :

=Les dossiers qui ont été analysés

/var/log/apache2 qui contient les fichier access.log  error.log  other_vhosts_access.log qui ont été analysés
*error.log est l'endroit où les informations concernant les erreurs ou les anomalies sont enregistrées 
/home/henry/FORENSIC_TP_EKWALA_HENRY/TP03/Images/errorlog.PNG
*access.log sert à la journalisation de tous les accès au serveur, c'est-à-dire toutes les requêtes HTTP reçues et la façon dont elles ont été traitées contenant l'adresse la date l'heure le port la requete effectuée et plein d'autres
/home/henry/FORENSIC_TP_EKWALA_HENRY/TP03/Images/accesslog.PNG

Listes des adresses ip à l'origine de la demande au serveur :
194.165.16.71
159.223.196.15
185.254.196.223
66.240.192.138 
143.110.234.221 
185.74.5.84 
20.206.73.93 
2.57.122.209 
188.166.232.196
174.138.61.80 
138.66.89.12 
152.89.196.211 
104.243.33.163 avec le code 405 qui signifie que la methode de requete est non autorisée ce qui fait de cette adresse un suspect

D'après l'analyse de tous ces fichiers, l'attaquant a efféctué de multiples requete au serveur et a finalement accéder jusqu'à  mettre en place un acces spécifique pour lui sur notre serveur web



*other_vhosts_access.log ne contient aucune information

/var/log/apt qui contient les informations sur les mises à jour


=les fichiers qui ont été analysés

alternatives.log
/home/henry/FORENSIC_TP_EKWALA_HENRY/TP03/Images/alternativelog.PNG

bootstrap.log
/home/henry/FORENSIC_TP_EKWALA_HENRY/TP03/Images/bootstraplog.PNG

btmp enregistre les tentatives de connexion infructueuses
dpkg.log pour la journalisation des paquets
faillog por les tentatives de connexions echouées
lastlog pour la derniere tentative de connexion
wtmp

                          Resultats

On constate qu'il y'a plusieurs erreurs de requete au niveau du serveur web




                         conclusion

En Conclusion de l'analyse les objectifs ont  été remplis car les données receuillies sont  suffisantes 




                         Recommandations

Pour renforcer la sécurité informatique faudra tout d'abord sécuriser son serveur web apaches en https au lien de http
bloquer tous les ports et connexions  non autorisées sur le serveur web
prevoir un reverse proxy pour le serveur web
mettre en place un serveur d'authentification


                         Conclusion générale 

En conclusion il etait question de de fiare une analyse forensique de cyber-bosh qui a été victime d'une attaque.
Cette analyse nous a permis d'illustrer toutes les vulnérabiltés de notre systèmes et y faire des recommandations.
l'analyse complete du repertoire /var/log et ses sous repertoires et fichiers nous a permis de retrouver les traces de l'attaquant de notre système et pouvoir mettre en place une sécurité plus fiable. 
