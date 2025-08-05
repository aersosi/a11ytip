# a11ytip

---

## Installation

1. a11ytip installieren:
   ```bash
   npm install a11ytip
   ```

2. CSS importieren:
   ```css
   @import "a11ytip/src/a11ytip.css";
   ```

   CSS (minified) importieren:
   ```css
   @import "a11ytip/dist/a11ytip.min.css";
   ```

3. Typescript importieren:
   ```typescript
   import { toggleA11ytip } from "a11ytip/src/ToggleA11ytip";
   
   document.addEventListener("DOMContentLoaded", toggleA11ytip);
   ```

   Typescript (minified) importieren:
   ```typescript
   import { toggleA11ytip } from "a11ytip/dist/ToggleA11ytip.min.js";
   
   document.addEventListener("DOMContentLoaded", toggleA11ytip);
   ```

---

## Anwendung

**Einfachstes Beispiel:**

```html
<button data-a11ytip-top aria-label="Hover mich">Hover mich</button>
```

---

## Positionierung

```html
<button data-a11ytip-top aria-label="Ich erscheine oben!">Hover mich</button>
<button data-a11ytip-top-left aria-label="Ich bin oben links ausgerichtet!">Hover mich</button>
<button data-a11ytip-top-right aria-label="Ich bin oben rechts ausgerichtet!">Hover mich</button>

<button data-a11ytip-right aria-label="Ich erscheine rechts!">Hover mich</button>
<button data-a11ytip-right-top aria-label="Ich bin rechts oben ausgerichtet!">Hover mich</button>
<button data-a11ytip-right-bottom aria-label="Ich bin rechts unten ausgerichtet!">Hover mich</button>

<button data-a11ytip-bottom aria-label="Ich erscheine unten!">Hover mich</button>
<button data-a11ytip-bottom-left aria-label="Ich bin unten links ausgerichtet!">Hover mich</button>
<button data-a11ytip-bottom-right aria-label="Ich bin unten rechts ausgerichtet!">Hover mich</button>

<button data-a11ytip-left aria-label="Ich erscheine links!">Hover mich</button>
<button data-a11ytip-left-top aria-label="Ich bin links oben ausgerichtet!">Hover mich</button>
<button data-a11ytip-left-bottom aria-label="Ich bin links unten ausgerichtet!">Hover mich</button>
```

---

## a11ytip Text

1. Der Text eines a11ytip wird primär über das `aria-label` definiert.
2. **Opt-Out:** Alternativ können Sie das `data-a11ytip-text`-Attribut nutzen.
3. Beide Attribute, `aria-label` und `data-a11ytip-text`, können gleichzeitig verwendet werden. In diesem Fall hat der
   Text aus `data-a11ytip-text` Vorrang und wird angezeigt.

**Beispiel mit beiden Attributen:**

```html
<button data-a11ytip-top
        aria-label="Schließe das Dialogfenster"
        data-a11ytip-text="Dialog schließen"
>
    Schließen
</button>
```

Das `data-a11ytip-text` definiert den angezeigten a11ytip-Text ("Dialog schließen"), während das `aria-label` weiterhin
für Barrierefreiheit verwendet werden kann.

---

## Aktiv-Status erzwingen

Mit der Eigenschaft `data-a11ytip-active` kann der aktive Status eines a11ytip permanent erzwungen werden, ohne dass ein
Hover-Ereignis erforderlich ist.

**Beispiel:**

```html
<button data-a11ytip-top
        data-a11ytip-active
        aria-label="Ich bin immer sichtbar!"
>
    Kein Hover nötig
</button>
```

---

## Konfiguration der a11ytips mit a11ytip_config.css

- Überschreiben Sie die Standartkonfiguration nach Ihren Bedürfnissen.
- Die CSS-Variablen sind selbsterklärend und steuern die Eigenschaften aller a11ytips.
- Alle typischen Farb-, Zeit- und Größenwerte können verwendet werden, z. B. #fafafa, 2s, px usw.

**Standartkonfiguration:**

```css
/* src/a11ytip_config.css */

:root {
    /* Text */
    --a11ytip-text-size: 1rem;
    --a11ytip-text-color: white;

    /* Box */
    --a11ytip-bg-color: var(--color-base-700, black);
    --a11ytip-padding-x: 0.375rem;
    --a11ytip-padding-y: 0.5rem;
    --a11ytip-border-radius: 0.375rem;
    --a11ytip-max-width: 14ch;

    /* Animation */
    --a11ytip-start-position: calc(100% + 4px);
    --a11ytip-end-position: calc(100% + 12px);
    --a11ytip-transition-duration: 350ms;
}

/* Dark Theme */
@media (prefers-color-scheme: dark) {
    :root:not(.light, [data-light], [data-theme="light"]) {
        --a11ytip-text-color: black;
        --a11ytip-bg-color: var(--color-base-100, white);
    }
}

[data-dark],
[data-theme="dark"],
:root.dark {
    --a11ytip-text-color: black;
    --a11ytip-bg-color: var(--color-base-100, white);
}
```

**Tailwind-Konfiguration Beispiel:**

```css
/* src/a11ytip_config.css */

:root {
    /* Text */
    --a11ytip-text-size: theme(fontSize.sm, 0.875rem);
    --a11ytip-text-color: theme(colors.white, #ffffff);

    ...
}

```

## Dark Theme und benutzerdefinierte Themes

Sie können das Dark Theme mit folgenden vordefinierten Selektoren nutzen:

- `data-dark` Attribut: `<body data-dark>`
- `data-theme="dark"` Attribut: `<body data-theme="dark">`
- `.dark` Klasse: `<body class="dark">`

Sie können auch eigene benutzerdefinierte Themes erstellen, indem Sie neue Selektoren in der `a11ytip_config.css`
definieren.

**Zum Beispiel:**

```css
/* Benutzerdefiniertes Pink-Theme */

[data-theme="pink"] {
    --a11ytip-text-color: white;
    --a11ytip-bg-color: darkmagenta;
}
```

## Anpassen von a11ytip mit Data-Attributen

Die CSS a11ytip unterstützen optionale `data-*` Attribute, die es Ihnen ermöglichen, die Standardstile eines einzelnen
a11ytip zu überschreiben.

**Verfügbare Data-Attribute:**

1. `data-a11ytip-*`:
    - Bestimmen, wo das a11ytip relativ zum Element erscheint.
    - Verfügbare Positionen:
        - `data-a11ytip-top` (zentriert)
        - `data-a11ytip-top-left`
        - `data-a11ytip-top-right`
        - `data-a11ytip-right` (zentriert)
        - `data-a11ytip-right-top`
        - `data-a11ytip-right-bottom`
        - `data-a11ytip-bottom` (zentriert)
        - `data-a11ytip-bottom-left`
        - `data-a11ytip-bottom-right`
        - `data-a11ytip-left` (zentriert)
        - `data-a11ytip-left-top`
        - `data-a11ytip-left-bottom`
    - Werteformat: Keine Werte erforderlich, die bloße Anwesenheit des Attributs aktiviert die entsprechende Position.

2. `data-a11ytip-text`:
    - Definiert den Textinhalt des a11ytip.
    - Dieses Attribut hat Vorrang vor `aria-label`, wenn beide vorhanden sind.
    - Werteformat: Beliebige Textzeichenfolge.

3. `data-a11ytip-text-size`:
    - Passt die Schriftgröße des a11ytip-Texts an.
    - Werteformat: `<Zahl>` gefolgt von einer Einheit (z.B. `16px`, `1rem`).

4. `data-a11ytip-text-color`:
    - Ändert die Farbe des a11ytip-Texts.
    - Werteformat: Ein gültiger CSS `<color>` Wert (z.B. `#ffffff`, `rgb(255, 255, 255)` oder `blue`).

5. `data-a11ytip-bg-color`:
    - Verändert die Hintergrundfarbe des a11ytip.
    - Werteformat: Ein gültiger CSS `<color>` Wert.

6. `data-a11ytip-padding-x` und `data-a11ytip-padding-y`:
    - Passt den horizontalen (`x`) und vertikalen (`y`) Innenabstand der a11ytip-Box an.
    - Werteformat: Ein CSS `<length>` Wert (z.B. `0.5rem`, `8px`).

7. `data-a11ytip-border-radius`:
    - Setzt den Rahmenradius der a11ytip-Box für abgerundete Ecken.
    - Werteformat: Ein CSS `<length>` Wert (z.B. `0.375rem`, `5px`).

8. `data-a11ytip-max-width`:
    - Setzt die maximale Breite der a11ytip-Box.
    - Dies verhindert, dass extrem lange Inhalte das a11ytip überdehnen.
    - Werteformat: Ein CSS `<length>` Wert (z.B. `14ch`, `150px`).
    - Standardwert: `14ch` (etwa 12 Zeichen breit).

9. `data-a11ytip-start-position` und `data-a11ytip-end-position`:
    - Positioniert das a11ytip beim Erscheinen (`start`) oder wenn es aktiv wird (`end`).
    - Werteformat: CSS `<length>` Werte (z.B. `4px`, `2rem`).

10. `data-a11ytip-transition-duration`:
    - Passt die Übergangsdauer des a11ytip an.
    - Werteformat: Eine gültige Zeitdauer (z.B. `350ms`, `0.5s`).

11. `data-a11ytip-delay`:
    - Ändert die Verzögerung bis das a11ytip angezeigt wird.
    - Werteformat: Eine Zahl in Millisekunden (z.B. `250`, `1000`).
    - Standardwert: `500` (500 Millisekunden).

12. `data-a11ytip-active`:
    - Erzwingt den aktiven Status eines a11ytip permanent, ohne dass ein Hover-Ereignis erforderlich ist.
    - Nützlich für die Überprüfung der Positionierung oder während der Entwicklung.
    - Werteformat: Keine Werte erforderlich, die bloße Anwesenheit des Attributs aktiviert den Effekt.

---

**Beispiel mit allen verfügbaren Data-Attributen:**

```html
<button data-a11ytip-top
        aria-label="Ich bin ein freches a11ytip!"
        data-a11ytip-text="Dieser text wird angezeigt"

        data-a11ytip-active

        data-a11ytip-text-size="2rem"
        data-a11ytip-text-color="hotpink"
        data-a11ytip-bg-color="#1a1a1a"
        data-a11ytip-padding-x="1rem"
        data-a11ytip-padding-y="0.8rem"
        data-a11ytip-border-radius="1rem"
        data-a11ytip-max-width="20ch"
        data-a11ytip-start-position="4px"
        data-a11ytip-end-position="12px"
        data-a11ytip-transition-duration="200ms"
        data-a11ytip-delay="1000"
>
    Hover mich
</button>
```