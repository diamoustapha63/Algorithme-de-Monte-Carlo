# Simulation Monte Carlo – Mouvement Brownien Géométrique (GBM)

## Description

Ce projet implémente une simulation Monte Carlo de l’évolution du prix d’un actif financier sur un horizon de 8 mois à l’aide d’un mouvement brownien géométrique (Geometric Brownian Motion).

L’objectif est d’estimer la distribution empirique des rendements à horizon fixe et d’en déduire plusieurs indicateurs de risque.

Ce modèle constitue la base théorique du modèle de Black-Scholes et représente l’approche standard en finance quantitative pour modéliser les prix d’actifs sous volatilité constante.

---

## Cadre mathématique

Le prix de l’actif suit la dynamique :

dS_t = μ S_t dt + σ S_t dW_t

où :

- μ : rendement annuel attendu
- σ : volatilité annuelle
- W_t : mouvement brownien standard

La solution analytique est :

S_T = S_0 exp((μ − ½σ²)T + σ W_T)

Dans la simulation discrète :

S_{t+1} = S_t exp((μ − ½σ²)Δt + σ√Δt Z)

avec :

- Z ~ N(0,1)
- Δt = T / n_steps

---

## Paramètres

| Paramètre | Description |
|-----------|------------|
| S0 | Prix initial |
| μ | Rendement annuel attendu |
| σ | Volatilité annuelle |
| T | Horizon temporel (8 mois recommandé : 8/12) |
| n_simulations | Nombre de trajectoires simulées |
| n_steps | Nombre de pas de discrétisation |

Exemple cohérent :

- μ = 0.08  
- σ = 0.20  
- T = 8/12  

---

## Méthodologie

1. Génération de 10 000 trajectoires indépendantes
2. Discrétisation du processus en 160 jours de trading
3. Calcul des prix finaux à horizon 8 mois
4. Construction de la distribution empirique des rendements

---

## Indicateurs de risque calculés

- Rendement médian
- Rendement moyen
- Value at Risk 5%
- Probabilité de perte > 20%
- Probabilité de gain > 30%

---

## Visualisations

Le script génère :

1. 100 trajectoires simulées
2. Histogramme de la distribution des rendements
   - médiane
   - VaR 5%

---

## Technologies

- Python
- NumPy
- Matplotlib

---

## Lancer le projet

```bash
python main.py
