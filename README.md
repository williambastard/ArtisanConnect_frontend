# Architecture adoptée
Nous utiliseront une architecture clean de type MVI ( Model-View-Intent )
![WhatsApp Image 2024-11-14 à 13 32 45_12efaaca](https://github.com/user-attachments/assets/234ddbfa-3146-454f-8139-f31d031c58d4)

Explication des dossiers:

data: Similaire à l'exemple Android, mais avec des "datasources" pour l'accès aux données (local/remote).
domain: Contient les "entities" qui représentent les objets métier, ainsi que les interfaces des repositories et les use cases.
presentation: Ici, on utilise des Widgets Flutter pour la partie UI.
user_view.dart: Le widget qui affiche l'interface utilisateur et interagit avec le ViewModel.
user_viewmodel.dart: Gère l'état de l'écran et traite les intents.
user_intent.dart: Représente les actions de l'utilisateur (ex: charger un utilisateur, rafraîchir la liste).
user_state.dart: Représente l'état de l'écran (ex: chargement, succès, erreur).
Spécificités Flutter:

Pas de "Activities" comme sur Android, on utilise des Widgets.
On peut utiliser des packages comme flutter_bloc ou riverpod pour faciliter la gestion de l'état (MVI).
L'injection de dépendances peut être gérée avec get_it ou provider.
Remarques:

Cette structure est une suggestion, il existe plusieurs façons d'organiser un projet Flutter avec Clean Architecture + MVI.
L'important est de respecter les principes de séparation des couches et de flux de données unidirectionnel.
