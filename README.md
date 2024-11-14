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
