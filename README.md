# Atlas · Spectres tumoraux

Aide-mémoire d'oncogénétique pour la consultation : quel gène donne quelles tumeurs, avec quels risques, quels variants récurrents, quelle surveillance et quel conseil génétique.

Fichier unique (`index.html`) sans dépendance : il s'ouvre hors ligne par double-clic ou se publie tel quel (GitHub Pages…).

## Vues

| Onglet | Usage |
|---|---|
| **Syndromes** | Cartes filtrables (catégorie, transmission). La recherche accepte plusieurs mots (« sein estomac »), un gène, un organe ou un variant (« c.1643 »). Les fiches consultées récemment apparaissent dans la barre latérale. |
| **Par organe** | Toutes les tumeurs héréditaires d'un organe, triées par risque, avec la **liste des gènes impliqués** (base indicative d'un panel, copiable). |
| **Par gène** | Risques propres au gène, variants récurrents, phénotype biallélique, liens (ClinVar, gnomAD, OMIM, GeneReviews, ClinGen, LOVD) et **interrogation en direct de ClinVar** (variants P/LP les plus soumis). |
| **Diagnostic** | Localisations tumorales **et signes non tumoraux** (taches café-au-lait, macrocéphalie, pneumothorax, consanguinité…) → syndromes compatibles classés. |
| **Matrice** | Vue d'ensemble syndromes × organes (intensité = risque maximal). |

## Fiche syndrome

Spectre tumoral avec un repère du risque en population générale (SEER), gènes, variants fondateurs (liens ClinVar), **conseil génétique** (âge du test chez l'enfant, mode de transmission, conseil reproductif biallélique, cascade, information de la parentèle), critères de test, surveillance, implications thérapeutiques, sources.

Actions : copier le lien, **copier la fiche en texte** (pour un compte-rendu ou un courrier), imprimer / PDF.

Chaque vue a sa propre URL (`#/gen/BRCA2`, `#/org/Rein`, `#/syn?f=lynch`, `#/diag?o=…`) : on peut la partager ou l'ajouter aux favoris, et le bouton Retour fonctionne.

## Modifier les données

Tout est dans `index.html`, dans le tableau `DATA` (un objet par syndrome) :

```js
{id, nom, al:[alias], cat, pre:"fréquence", tr:"transmission",
 genes:[[symbole, rôle]],
 sp:[[tumeur, [organes], "risque (texte)", valeur_numérique|null, note]],
 va:[[variant, commentaire]], cr:[critères], su:[surveillance], tt:[traitements], src:[sources]}
```

- Ajouter « — GÈNE » à la fin du nom d'une tumeur (`"Ovaire — BRCA1"`) la rattache à ce gène sur la page du gène et dans les listes de gènes par organe.
- Les données de conseil propres à chaque syndrome sont dans `CG` ; les phénotypes bialléliques dans `BIAL` ; les signes cliniques du diagnostic différentiel dans `SIGNS` ; les repères de population dans `POP`.

> Outil d'aide à la consultation : les chiffres sont des estimations issues de cohortes. Vérifier les référentiels en vigueur et discuter en RCP avant toute décision.
