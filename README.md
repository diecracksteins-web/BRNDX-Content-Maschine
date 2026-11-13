# BRNDX.intelligence HQ

Die Steuerzentrale von BRNDX.media: ein 3D-Büro mit 8 KI-Abteilungen (Strategie, Grafik, Content, Growth, Research, Web, Kundenservice, Finanzen).

Die App läuft als Claude-Artefakt (`hq/index.html`) und nutzt dort:
- `sample` für die KI-Abteilungen,
- `db` für Aufträge, Marken-Profile und abgelehnte Entwürfe,
- `mcp` für Metricool (geplante Posts lesen, Entwürfe freigeben) und die geplanten Claude-Aufgaben (Autopilot).

## Ablauf eines Auftrags
1. **Strategie** schreibt ein kurzes Briefing.
2. Die **Fachabteilung** arbeitet den Auftrag mit dem Marken-Profil aus.
3. Der **QA-Agent** prüft: feste Regeln im Code (`hardCheck`) und eine zweite KI-Prüfung (`qaCheck`). Bei Mängeln gibt es eine Überarbeitung, danach Sperre.
4. Bestandenes geht in **Freigaben**. Nichts wird ohne Freigabe veröffentlicht.

## Harte Regeln (QA)
- Keine erfundenen Zahlen, Kunden, Referenzen; keine Preise oder Garantien in öffentlichen Texten.
- Marken ohne Cannabis-Flag: kein Cannabis-Bezug.
- Cannabis-Marken (z. B. @talkingbubatz420): deutsches Recht (KCanG, HWG, JuSchG), nichts für Minderjährige, kein Konsum- oder Kaufanreiz, keine Dosierungen, Bezugsquellen, Preise oder Heilversprechen, Hinweis „ab 18“ Pflicht.

## Marken-Profile (Brand-Memory, mandantenfähig)
Collection `brands` in der Artefakt-Datenbank: `name, handle, metricoolId, autopilotId, about, audience, tone, ctas, nogos, topPosts, learnings, cannabis`.
Der Content-Autopilot liest das Profil vor jedem Lauf und schreibt montags die Erkenntnisse aus den Metricool-Zahlen nach `learnings`.

## Secrets
Keine API-Keys im Code. Alle Zugänge laufen über die Claude-Connectors des jeweiligen Nutzers.
