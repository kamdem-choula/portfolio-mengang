# Projet Mengang — Étude analytique d'un projet agricole camerounais

> 35 mois d'activité agricole décryptés sous l'angle financier, opérationnel et commercial. 21 M XAF investis, 2,3 M XAF de revenus, 592 transactions classifiées ligne par ligne. Un cas pratique de lecture comptable et de quantification du risque opérationnel en contexte rural.

🔗 https://github.com/kamdem-choula/portfolio-mengang.git

📁 **Trois livrables** : Dashboard HTML interactif · Workbook Excel · Deck PowerPoint

\---

## Contexte

Le Projet Mengang est une plantation de **5,7 hectares dans la région centre du Cameroun** (département du Nyong et Mfoumou), en activité depuis mai 2023. Trois cultures principales : plantain (*Musa paradisiaca*), macabo (*Xanthosoma sagittifolium*) et gombo (*Abelmoschus esculentus*).

La période sous analyse couvre **35 mois (mai 2023 → mai 2026)**. Les données proviennent du ledger interne du projet : 592 lignes de dépenses, 12 ventes, 8 catégories d'activité. Devise : franc CFA (XAF).

Le cas est analytiquement intéressant parce qu'il combine quatre dimensions qu'on retrouve dans les analyses de microfinance, d'assurance agricole et d'évaluation de projets de coopération :

* Un **investissement initial massif** (caution foncière, défrichement, plantation)
* Une **récurrence opérationnelle** (main-d'œuvre, intrants, transport)
* Un **risque opérationnel quantifiable** (vol agricole — 8,6 % des récoltes)
* Une **structure commerciale concentrée** (un transporteur unique, top 5 récipiendaires à 41 %)

\---

## Indicateurs clés

|Indicateur|Valeur|Lecture|
|-|-:|-|
|Investissement total|**21 156 550 XAF**|592 transactions sur 35 mois|
|Revenus encaissés|2 312 100 XAF|10,9 % de récupération|
|Part CapEx|63,5 %|13 431 650 XAF immobilisés|
|**ROI brut**|**−89,1 %**|Vue pessimiste, tout traité comme charge|
|**ROI opérationnel**|**−70,1 %**|Hors CapEx (IAS 41)|
|**ROI amorti**|**−77,4 %**|OpEx + dotation pro rata|
|Pertes par vol|217 K XAF|8,6 % des revenus · 64 régimes|
|HHI récipiendaires|595|Concentration modérée|
|Tendance prix plantain|r = −0,82|Pression baissière nette sur 35 mois|
|Top dépense|Théophile (12,2 %)|Main-d'œuvre + intrants combinés|
|VNC actuelle|10,9 M XAF|81,3 % du CapEx encore portée au bilan|

\---

## Insights principaux

**1. Le ROI reste négatif sous les trois conventions comptables.** Contrairement à beaucoup de projets en ramp-up, la séparation CapEx/OpEx ne renverse pas le verdict ici — les unités économiques n'ont pas encore atteint le seuil de rentabilité opérationnelle, même en excluant l'investissement. C'est le diagnostic central : ce n'est pas un problème d'amortissement, c'est un problème de marge variable.

**2. Bebeto est un seul point d'échec du transport.** 100 % des évacuations vers les marchés urbains passent par un seul intermédiaire. Sa défaillance immobiliserait les récoltes périssables — plantain : 5 jours de fenêtre, gombo : 48 heures.

**3. Le prix du plantain s'effrite (r = −0,82).** Corrélation linéaire négative très forte entre la date et le prix unitaire de vente, probablement liée à l'arrivée de nouvelles productions concurrentes dans la région. Le projet doit chercher la valeur ailleurs : intégration aval (transformation), différenciation variétale, ou marchés à plus forte marge (Yaoundé direct vs intermédiaires).

**4. 64 régimes volés sur 886 récoltés (7,2 % en volume, 8,6 % en valeur).** Les vols ciblent les plus belles pièces, donc la perte en valeur excède la perte en quantité. Une surveillance ciblée pendant les 3 semaines pré-récolte couvrirait le risque sans surcoût permanent.

**5. Trois scénarios de retour à l'équilibre.** Conservateur (maintien actuel) : 6,3 ans. Réaliste (+30 % rendement par densification) : 3,5 ans. Optimiste (intégration aval + élimination des vols) : 2,0 ans. Le levier dominant est commercial, pas opérationnel.

\---

## Livrables

|Fichier|Description|Format|
|-|-|-|
|[`index.html`](./index.html)|Dashboard interactif 8 sections · 11 graphiques Chart.js · responsive|HTML autonome|
|[`02\\\\\\\\\\\\\\\_Workbook\\\\\\\\\\\\\\\_KPIs\\\\\\\\\\\\\\\_Mengang.xlsx`](./02_Workbook_KPIs_Mengang.xlsx)|8 feuilles · 109 formules vivantes · code couleur inputs/refs/totaux|Excel|
|[`03\\\\\\\\\\\\\\\_Portfolio\\\\\\\\\\\\\\\_Deck\\\\\\\\\\\\\\\_Mengang.pptx`](./03_Portfolio_Deck_Mengang.pptx)|11 slides format LAYOUT\_WIDE · palette terre/ocre/sauge|PowerPoint|

\---

## Méthodologie

```
Ingestion (openpyxl)
        ↓
Normalisation des dates, devises, taxonomies (pandas)
        ↓
Classification CapEx/OpEx ligne par ligne (IAS 16 / IAS 41)
        ↓
Calcul KPI : ROI × 3 vues · Pareto/ABC · HHI · corrélations
        ↓
Modélisation scénarios linéaires à 3 paramètres
        ↓
Restitution : HTML (Chart.js) · XLSX (formules vivantes) · PPTX (pptxgenjs)
```

**Stack technique** : Python 3.11 · pandas · openpyxl · numpy · Chart.js 4 · pptxgenjs · LibreOffice (validation des formules Excel par recalcul automatisé).

Chaque chiffre du dashboard est traçable jusqu'à une ligne du ledger source. Le workbook Excel n'a pas de valeur en dur sur les KPI calculés — toutes les formules sont vivantes et recalculables.

\---

## Limites documentées

> Une analyse honnête expose ses propres angles morts.

* **G1** · Pas de comptabilité analytique par culture — les coûts indirects sont alloués au prorata du chiffre d'affaires.
* **G2** · Mesures de rendement par hectare absentes — les comparaisons inter-cultures restent approximatives.
* **G3** · 12 transactions de vente seulement — modélisation prédictive non robuste statistiquement, intervalles de confiance larges.
* **G4** · Conventions d'amortissement IAS 41 simplifiées (pas de fair value reassessment annuel).
* **G5** · Pertes climatiques et phytosanitaires non isolées des écarts de rendement.

\---

## À propos

**Morel kamdem** —  Data Analyst ·

Étude de cas №01 d'un portfolio bilingue (français + anglais) qui couvre l'agriculture, l'industrie manufacturière (cf. [étude №02 — NorthLine Assembly](#)), et d'autres contextes à venir. Construit pour démontrer une capacité analytique reproductible à travers des domaines opérationnels divers — la méthode prime sur le secteur.

📧 mail to: kamdemchoula@gmail.com · 🔗 \[LinkedIn] · 📂 [https://github.com/kamdem-choula/portfolio-mengang.git](#)

## Reproduire l'analyse

Pour ouvrir le dashboard directement :

```bash
git clone https://github.com/kamdem-choula/portfolio-mengang.git
cd portfolio-mengang
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows


