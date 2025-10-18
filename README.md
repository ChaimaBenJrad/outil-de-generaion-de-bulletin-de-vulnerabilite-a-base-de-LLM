# Développement d'un outil de génération de bulletin de vulnérabilité à base de LLM

## Description du projet
Ce projet vise à développer un outil intelligent capable de **générer automatiquement des bulletins de vulnérabilité informatique** à partir de données issues de sources publiques.  
Le cœur du système repose sur le modèle **[LLaMA 3](https://llama.meta.com/llama3/)**, utilisé pour comprendre et reformuler les informations de cybersécurité sous un format standardisé et clair.

---

## Étapes principales du projet

1. **Déploiement de LLaMA 3**  
   - Chargement du modèle pré-entraîné  
   - Configuration de l’environnement GPU (le projet est exécuté sur **Google Colab** pour profiter de ressources matérielles supplémentaires)

2. **Scraping de la source**  
   - Collecte automatique des bulletins de sécurité depuis une source publique

3. **Nettoyage et préparation des données**  
   - Suppression des doublons et des données incomplètes. 
   - Structuration des descriptions de vulnérabilités avant envoi au modèle

4. **Prompt de génération**  
   ```python
   inputs = tokenizer(
       [
           prompt.format(
               "Tu es un assistant de cybersécurité. Les utilisateurs vont te donner la description d'une vulnérabilité informatique en français ou en anglais et tu vas générer pour la vulnérabilité informatique son titre, ses impacts, les plateformes, les logiciels impactés, les solutions et une documentation additionnelle, tout cela doit être en français, sous cette forme: Description: description ici. Titre: titre ici. Impacts: impacts ici. Plateformes: plateformes ici. Logiciels impactés: Logiciels impactés ici. Solutions: solution ici, détails de la solution ici, lien de la solution ici. Documentation additionnelle: Documentation additionnelle ici",
               cve['description'],
               "",
           )
       ], return_tensors="pt"
   ).to("cuda")
   ```

5. **Entraînement et publication du modèle**  
   - Fine-tuning du modèle LLaMA 3 sur les descriptions collectées
   - Upload du modèle sur **Hugging Face** pour utilisation publique  

6. **Génération des bulletins HTML/CSS**  
   - Génération automatique d’une **liste de bulletins** avec liens vers les **détails complets**
   - Mise en page claire et responsive

---

## Technologies utilisées
- **Python** (scraping, nettoyage, génération HTML)
- **Transformers**
- **Requests** (scraping)
- **HTML / CSS** (rendu des bulletins)

---

Pour des raisons de **sécurité et de confidentialité**, le code source complet de cette application n’est pas publié sur ce dépôt.
Toutefois, **l’intégralité du code est disponible localement** et peut être présentée ou démontrée sur demande, notamment dans le cadre d’un **entretien ou d’une évaluation technique**.

## Auteur
**Shayma Ben Jrad**  
Projet de stage – 2024 
