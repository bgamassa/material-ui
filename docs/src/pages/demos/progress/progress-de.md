---
title: Zirkulärer Fortschritt, Linearer Fortschritt React Komponente
components: CircularProgress, LinearProgress
---
# Fortschritt

<p class="description">Fortschrittsanzeigen geben eine unbestimmte Wartezeit oder die Länge eines Prozesses an.</p>

[Fortschrittsanzeigen](https://material.io/design/components/progress-indicators.html) informieren Benutzer über den Status laufender Prozesse, z. B. Laden einer App, Senden eines Formulars oder Speichern von Updates. Sie kommunizieren den Status der App und zeigen verfügbare Aktionen an, beispielsweise, ob Benutzer vom aktuellen Bildschirm weg navigieren können.

**Bestimmte** Indikatoren zeigen an, wie lange eine Operation dauert.

**Unbestimmt** Indikatoren visualisieren eine nicht angegebene Wartezeit.

#### Fortschritt als Gruppe

Wenn Sie den Fortschritt für eine Folge von Prozessen anzeigen, geben Sie den Gesamtfortschritt und nicht den Fortschritt der einzelnen Aktivitäten an.

## Circular

[Zirkulärer Fortschritt](https://material.io/design/components/progress-indicators.html#circular-progress-indicators) unterstützt sowohl bestimmte als auch unbestimmte Prozesse.

- **Bestimmte** zirkuläre Fortschritte füllen die unsichtbare, kreisförmige Spur mit Farbe, wenn sich der Indikator von 0 bis 360 Grad bewegt.
- **Unbestimmte** zirkuläree Fortschritte vergrößern und verkleinern sich, während sie sich entlang der unsichtbaren Spur bewegen.

### Zirkular Unbestimmt

{{"demo": "pages/demos/progress/CircularIndeterminate.js"}}

### Interaktive Integration

{{"demo": "pages/demos/progress/CircularIntegration.js"}}

### Zirkular Bestimmt

{{"demo": "pages/demos/progress/CircularDeterminate.js"}}

### Zirkular Statisch

{{"demo": "pages/demos/progress/CircularStatic.js"}}

## Linear

[Linearer Fortschritt](https://material.io/design/components/progress-indicators.html#linear-progress-indicators) Indikator.

### Linear Unbestimmt

{{"demo": "pages/demos/progress/LinearIndeterminate.js"}}

### Linear Bestimmt

{{"demo": "pages/demos/progress/LinearDeterminate.js"}}

### Linearer Puffer

{{"demo": "pages/demos/progress/LinearBuffer.js"}}

### Linear Abfrage

{{"demo": "pages/demos/progress/LinearQuery.js"}}

## Nicht-standardmäßige Bereiche

Die Fortschrittskomponenten akzeptieren einen Wert im Bereich von 0 - 100. Dies vereinfacht die Benutzer von Bildschirmleseprogrammen, wenn dies die voreingestellten Min / Max-Werte sind. Manchmal arbeiten Sie jedoch mit einer Datenquelle, bei der die Werte außerhalb dieses Bereichs liegen. So können Sie einen Wert in einem beliebigen Bereich auf eine Skala von 0 - 100 leicht umwandeln:

```jsx
// MIN = Minimaler erwarteter Wert
// MAX = Maximaler erwarteter Wert
// Funktion zur Normalisierung der Werte (MIN / MAX kann integriert werden)
const normalize = Wert => (Wert - MIN) * 100 / (MAX - MIN.));

// Beispielkomponente, die an der Stelle des Renderns die Funktion "normalise" verwendet.
function Progress(props) {
  return (
    <React.Fragment>
      <CircularProgress variant="determinate" value={normalise(props.value)} />
      <LinearProgress variant="determinate" value={normalise(props.value)} />
    </React.Fragment>
  )
}
```

## Individueller Fortschritt

Wenn du die [Overrides Dokumentationsseite](/customization/overrides/) gelesen hast, aber dich noch nicht sicher genug fühlst, um direkt loszulegen, ist hier noch ein Beispiel, wie du die Komponenten anpassen könntest. Die letzte Demo zeigt, wie Sie einen Facebook-ähnlichen Spinner erstellen können.

⚠️ Auch wenn die material design Spezifikation zur Verwendung von Themes ermutigt, liegen diese Beispiele außerhalb der üblichen Pfade.

{{"demo": "pages/demos/progress/CustomizedProgress.js"}}

## Erscheinung verzögern

Es gibt [3 wichtige Grenzwerte](https://www.nngroup.com/articles/response-times-3-important-limits/), um die Reaktionszeit zu kennen. Der Ripple Effekt der `ButtonBase` Komponente stellt sicher, dass der Benutzer das Gefühl hat, dass das System sofort reagiert. Normalerweise ist keine spezielle Rückmeldung bei Verzögerungen von mehr als 0,1 Sekunden und weniger als 1,0 Sekunden erforderlich. Nach 1,0 Sekund können Sie einen Fortschritt anzeigen, um den Gedankenfluss des Benutzers nicht zu unterbrechen.

{{"demo": "pages/demos/progress/DelayingAppearance.js"}}

## Einschränkungen

Bei starker Belastung verlieren Sie möglicherweise die Strich-Animation oder sehen zufällige CircularProgress-Ringbreiten. Sie sollten prozessorintensive Vorgänge in einem Web-Worker oder in Batches ausführen, um den Haupt-Rendering-Thread nicht zu blockieren.

![schwere Last](/static/images/progress/heavy-load.gif)

Wenn dies nicht möglich ist, können Sie die `disableShrink` Eigenschaft nutzen, um das Problem zu verringern. Siehe https://github.com/mui-org/material-ui/issues/10327

{{"demo": "pages/demos/progress/CircularUnderLoad.js"}}