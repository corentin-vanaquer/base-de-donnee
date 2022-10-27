# Dictionnaire de données

## Carte
| Champ | Type | Spécificités | Description |
|--|--|--|--|
| codeCarte |INT| GENERATED ALWAYS AS IDENTITY PRIMARY KEY | L’identifiant de la carte |
| titre | TEXT | NOT NULL UNIQUE | Le titre de la carte |
| position | INT | NOT NULL DEFAULT 0 | La position de la carte |
| couleur | TEXT | NOT NULL DEFAULT '#ffffff' | La couleur de la carte |
| codeListe | INT | NOT NULL REFERENCES list(id) ON DELETE CASCADE | L’identifiant de la liste |
| creer_le | TIMESTAMPTZ | NOT NULL DEFAULT NOW() | La date de création de la carte |
| mis_a_jour_le|TIMESTAMPTZ | | La date de dernière modification de la carte |

## Label
| Champ | Type | Spécificités | Description |
|--|--|--|--|
| codeLabel | INT | GENERATED ALWAYS AS IDENTITY PRIMARY KEY | L’identifiant du label |
| nom | TEXT | NOT NULL UNIQUE | Le nom du label |
| couleur | TEXT | NOT NULL DEFAULT '#ffffff' | La couleur du label |
| creer_le | TIMESTAMPTZ | NOT NULL DEFAULT NOW() | La date de création du label |
| mis_a_jour_le|TIMESTAMPTZ |  | La date de dernière modification du label |

## Liste
| Champ | Type | Spécificités | Description |
|--|--|--|--|
| codeListe| INT | GENERATED ALWAYS AS IDENTITY PRIMARY KEY | L’identifiant de la liste |
| nom | TEXT | NOT NULL UNIQUE | Le nom de la liste |
| position | INT | INTEGER NOT NULL DEFAULT 0 | La position de la liste |
| creer_le | TIMESTAMPTZ | NOT NULL DEFAULT NOW() | La date de création de la liste |
| mis_a_jour_le|TIMESTAMPTZ |   | La date de dernière modification de la liste |

## Possède
| Champ | Type | Spécificités | Description |
|--|--|--|--|
| codeCarte | INT | NOT NULL REFERENCES "card"(id) ON DELETE CASCADE | L’identifiant de la carte |
| codeLabel | INT | NOT NULL REFERENCES label(id) ON DELETE CASCADE | L’identifiant du label |
| creer_le | TIMESTAMPTZ | NOT NULL DEFAULT NOW() | La date de création du label |
| | | PRIMARY KEY (codeCarte, codeLabel) |

