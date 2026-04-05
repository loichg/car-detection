# Détection de voiture

Ce dépôt contient l'implémentation complète d'un détecteur de voitures basé sur l'architecture YOLOv8. Le modèle a été entraîné pour optimiser le compromis entre une inférence ultra-rapide (temps réel) et une précision de localisation élevée.

## Architecture du Modèle

Nous utilisons la version YOLOv8 Nano (n), la plus légère de la famille Ultralytics, idéale pour le déploiement sur des systèmes embarqués ou mobiles.
Nombre de couches : 129
Paramètres : 3,011,043
GFLOPs : 8.2
Input Resolution : 640x640 pixels

## Pipeline

Le dataset a subi un nettoyage rigoureux suite à l'identification de fichiers corrompus :
Volume Initial : 19 506 images.
Nettoyage Automatisé : Suppression de 11 064 fichiers labels mal formatés ou vides (classes incorrectes ou manque de coordonnées).
Volume Final : 14 276 images (Train: 11 429 | Val: 2 847).
Augmentation de données : Utilisation de Mosaic (activé par défaut), rotation, et ajustements HSV pour renforcer la robustesse face aux variations lumineuses.

## Configuration de l'Entraînement et performance

| Test # | Epochs | Batch size | Image size | Learning rate | Precision | Recall | F1 score | mAP\@0.5 | mAP\@0.5:0.95 |
|--------|--------|------------|------------|---------------|-----------|--------|----------|---------|---------------|
| 1      | 10     | 16         | 320        | 0.001         | 0.937     | 0.924  | 0.931    | 0.974   | 0.865         |
| 2      | 10     | 64         | 640        | 0.001         | 0.940     | 0.945  | 0.943    | 0.980   | 0.888         |
| 3      | 10     | 64         | 640        | 0.0005        | 0.944     | 0.942  | 0.943    | 0.980   | 0.890         |
| 4      | 10     | 32         | 640        | 0.0001        | 0.929     | 0.912  | 0.901    | 0.970   | 0.885         |


Parameters of test 3 + hyperparameters  
momentum = 0.95         
weight_decay = 0.0005    
Precision: 0.942    
Recall: 0.930  
F1 Score: 0.936  
mAP\@0.5: 0.978  
mAP\@0.5:0.95: 0.879  
    

Parameters of test 3 + hyperparameters   
momentum = 0.937       
weight_decay = 0.0005  
augment = True          
patience = 5          
optimizer = "SGD"    
Precision: 0.937    
Recall: 0.946   
F1 Score: 0.941      
mAP\@0.5: 0.978      
mAP\@0.5:0.95: 0.877     

## Evaluation

Precision: 0.937
Recall: 0.946
F1 Score: 0.941
mAP@0.5: 0.978
mAP@0.5:0.95: 0.877

## Résultat

<img width="636" height="504" alt="9eb00a03-13e4-4c36-8ced-42371d8285da" src="https://github.com/user-attachments/assets/66b3d53c-85cb-4694-9c28-05fec85d9a6c" />

<img width="636" height="504" alt="117a1aa0-80c4-4981-9e6b-f750951bff4f" src="https://github.com/user-attachments/assets/6c69671e-c1a1-48d9-990c-4816cd8eb9d2" />

<img width="636" height="504" alt="605b88f7-f0b1-47ee-acff-7072c62fe543" src="https://github.com/user-attachments/assets/0e78fed1-bcdc-457b-ae24-943bac85cd5e" />

<img width="636" height="504" alt="ec48af51-5ca8-42b2-b829-99c0a4ad0085" src="https://github.com/user-attachments/assets/7f49c945-9f30-4997-b290-f11d358f8b23" />
