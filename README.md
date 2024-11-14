# Architecture adoptée
Nous utiliseront une structure mixte ( layer-first + feature-first )
- lib/
  - features/
    - authentification/
      - presentation/
        - screens/
        - widgets/
        - blocs/
      - domain/
        - models/
        - repositories/
        - usecases/
      - data/
        - models/
        - sources/
        - repositories/
        - profil/
      - ...
  - shared/
    - ...
![image](https://github.com/user-attachments/assets/c87818c5-cae2-4a4f-8247-7cc60167f319)

Pour illustrer la structure "layer-first" en détail, prenons l'exemple d'une application de livraison de repas, "Food Delivery App".

## 1. Présentation (presentation)

**screens/**: Contient les widgets qui définissent l'interface utilisateur de chaque écran.

**home_screen.dart**: Affiche la liste des restaurants, plats populaires, et options de recherche. Utilise HomeViewModel pour obtenir les données et gérer les interactions utilisateur.

**restaurant_detail_screen.dart**: Affiche les détails d'un restaurant (menu, avis, informations). Utilise RestaurantDetailViewModel.

**cart_screen.dart**: Affiche le panier de l'utilisateur et gère la validation de la commande.

**order_history_screen.dart**: Affiche l'historique des commandes de l'utilisateur.

**widgets/**: Contient les widgets réutilisables dans l'application.

**restaurant_card.dart**: Affiche un restaurant sous forme de carte avec image, nom et note.

**dish_item.dart**: Affiche un plat avec image, nom, description et prix.

**bottom_navigation_bar.dart**: Widget pour la navigation principale de l'application.

**blocs/**: Contient les blocs qui gèrent la logique de présentation et le flux de données.

**home_bloc.dart**: Gère le chargement et l'affichage des restaurants, plats, etc. sur l'écran d'accueil.

**cart_bloc.dart**: Gère l'ajout, la suppression et la modification des éléments du panier.


## 2. Domaine (domain)

**models/**: Contient les modèles de données métier.

**restaurant.dart**: Définit la classe Restaurant avec ses attributs (nom, cuisine, adresse, note, etc.).

**dish.dart**: Définit la classe Dish (nom, description, prix, image, etc.).

**order.dart**: Définit la classe Order (éléments, prix total, adresse de livraison, etc.).

**repositories/**: Définit les interfaces des repositories.

**restaurant_repository.dart**: Interface pour accéder aux données des restaurants.

**order_repository.dart**: Interface pour gérer les commandes.

**usecases/**: Contient les cas d'utilisation qui implémentent la logique métier.
**get_restaurants_usecase.dart**: Récupère la liste des restaurants du repository.
**get_restaurant_details_usecase.dart**: Récupère les détails d'un restaurant spécifique.
**add_to_cart_usecase.dart**: Ajoute un plat au panier.
**place_order_usecase.dart**: Crée une nouvelle commande.
**get_order_history_usecase.dart**: Récupère l'historique des commandes de l'utilisateur.

## 3. Données (data)
**models/**: Contient les modèles de données spécifiques à la source de données.
**restaurant_dto.dart**: Définit la structure des données de restaurant pour la persistance (ex: format JSON pour une API).

**sources/**: Contient les implémentations pour accéder aux sources de données.
**restaurant_remote_data_source.dart**: Accède aux données des restaurants via une API distante (ex: avec http ou dio).
**order_local_data_source.dart**: Gère la persistance des commandes localement (ex: avec shared_preferences).

**repositories/**: Contient les implémentations concrètes des repositories.
**restaurant_repository_impl.dart**: Implémente RestaurantRepository en utilisant RestaurantRemoteDataSource.
**order_repository_impl.dart**: Implémente OrderRepository en utilisant OrderLocalDataSource.
Exemple détaillé: get_restaurants_usecase.dart

```dart
import '../repositories/restaurant_repository.dart';
import '../models/restaurant.dart';

class GetRestaurantsUseCase {
  final RestaurantRepository repository;

  GetRestaurantsUseCase({required this.repository});

  Future<List<Restaurant>> execute() async {
    return repository.getRestaurants();
  }
}
```
En appliquant cette structure "layer-first" à votre application "Food Delivery App", vous obtiendrez une base solide pour développer une application maintenable et évolutive. N'hésitez pas à adapter cette structure à vos besoins spécifiques.
