# Claude Code for Home Assistant

🤖 **Claude Code direkt in Home Assistant** - Ein modernes Web-Interface für Conversations mit Claude, vollständig integriert als Home Assistant Addon.

## ✨ Features

- **🌐 Web-Interface** - Moderne Chat-Oberfläche direkt in Home Assistant
- **🔗 MCP Integration** - Automatische Verbindung zum Claude MCP Server für Dateizugriff
- **📱 Responsive Design** - Funktioniert perfekt auf Desktop, Tablet und Smartphone
- **⚡ Real-time Updates** - WebSocket-Verbindung für Live-Status und Chat
- **🛡️ Enterprise Sicherheit** - Rate Limiting, Input Validation, Security Headers
- **🎨 Moderne UI** - Glassmorphism-Design mit Gradient-Hintergründen

![Claude Code Interface](https://raw.githubusercontent.com/DawidSu/ha-claude-code-addon/main/.github/screenshot.png)

## 📦 Installation

### 1. Repository hinzufügen

Füge diese URL zu deinen Home Assistant Add-on Repositories hinzu:

```
https://github.com/DawidSu/ha-claude-code-addon
```

**Schritte:**
1. Home Assistant → **Einstellungen** → **Add-ons**
2. **Add-on Store** → **⋮** (3 Punkte) → **Repositories**
3. URL eingeben: `https://github.com/DawidSu/ha-claude-code-addon`
4. **Hinzufügen** klicken

### 2. Addon installieren

1. **Add-on Store** → **Claude Code** suchen
2. **Installieren** klicken
3. Warten bis Installation abgeschlossen

### 3. Konfigurieren

**Wichtig:** Du benötigst einen **Anthropic API Key**:

1. Gehe zu [console.anthropic.com](https://console.anthropic.com)
2. Erstelle einen Account (kostenlos)
3. Generiere einen API Key
4. Kopiere den Key (beginnt mit `sk-ant-api03-...`)

**Addon-Konfiguration:**
```yaml
anthropic_api_key: "sk-ant-api03-DEIN-API-KEY"
model: "claude-3-5-sonnet-20241022"
max_tokens: 4096
auto_connect_mcp: true
mcp_server_host: "localhost"
mcp_server_port: 3000
log_level: "info"
```

### 4. Starten

1. **Konfiguration** → **Speichern**
2. **Start** klicken
3. **Web UI öffnen** klicken

## 🚀 Erste Schritte

### Quick Actions nutzen
Das Interface bietet vorgefertigte Buttons:

- 📁 **Konfiguration anzeigen** - Zeigt deine HA-Dateien
- ⚡ **Automation erstellen** - Hilft bei neuen Automationen  
- 🔍 **Fehlercheck** - Analysiert deine Konfiguration
- 🌙 **Script erstellen** - Erstellt neue Scripts

### Beispiel-Prompts

```
"Zeige mir meine Home Assistant Konfiguration"
"Erstelle eine Automation für den Flur-Bewegungsmelder"
"Analysiere meine automations.yaml auf Fehler"
"Schreibe ein Script für den Gute-Nacht-Modus"
"Optimiere meine Lovelace Dashboard Konfiguration"
"Welche Sensoren sind in der Küche definiert?"
```

## 🔧 Erweiterte Konfiguration

### Claude Modelle

| Modell | Beschreibung | Kosten | Empfehlung |
|--------|--------------|--------|------------|
| `claude-3-5-sonnet-20241022` | Beste Balance | Mittel | ✅ **Empfohlen** |
| `claude-3-5-haiku-20241022` | Schnell & günstig | Niedrig | Für einfache Fragen |
| `claude-3-opus-20240229` | Höchste Qualität | Hoch | Für komplexe Aufgaben |

### MCP Server Integration

Für **erweiterte Funktionalität** installiere auch den [Claude MCP Server](https://github.com/DawidSu/ha-mcp-server):

```yaml
auto_connect_mcp: true        # Automatische MCP Verbindung
mcp_server_host: "localhost"  # MCP Server Adresse  
mcp_server_port: 3000         # MCP Server Port
```

**Ohne MCP Server**: Chat funktioniert, aber kein Dateizugriff
**Mit MCP Server**: Vollzugriff auf Home Assistant Dateien

## 📱 Mobile Nutzung

Das Interface ist vollständig **responsive** und funktioniert perfekt auf:

- 📱 **Smartphones** - Touch-optimierte Bedienung
- 📋 **Tablets** - Große Chat-Ansicht
- 💻 **Desktop** - Vollständige Features

## 🛡️ Sicherheit

- **🔒 API Key Schutz** - Keys werden nicht geloggt oder angezeigt
- **⚡ Rate Limiting** - Schutz vor API-Missbrauch (10/min)
- **🛡️ Input Validation** - Alle Eingaben werden validiert
- **🔐 Security Headers** - Helmet.js für HTTP-Sicherheit
- **🌐 CORS Schutz** - Nur autorisierte Zugriffe erlaubt

## 🔍 Troubleshooting

### Häufige Probleme

#### ❌ "Claude ist nicht verfügbar"
**Ursache:** API Key fehlt oder ungültig
**Lösung:** 
1. API Key in Addon-Konfiguration prüfen
2. Key muss mit `sk-ant-api03-` beginnen
3. Bei console.anthropic.com neuen Key generieren

#### ❌ "MCP Server nicht erreichbar"
**Ursache:** Claude MCP Server nicht installiert/gestartet
**Lösung:**
1. [Claude MCP Server Addon](https://github.com/DawidSu/ha-mcp-server) installieren
2. MCP Server starten
3. Claude Code Addon neu starten

#### ❌ "Addon startet nicht"
**Lösung:**
```bash
# Logs prüfen in HA:
Einstellungen → Add-ons → Claude Code → Logs

# Häufige Ursachen:
- Port 8080 bereits belegt
- Ungültiger API Key
- Unvollständige Installation
```

#### ❌ "Langsame Antworten"
**Optimierung:**
- Zu `claude-3-5-haiku` wechseln (schneller)
- `max_tokens` auf 2048 reduzieren
- Kürzere Nachrichten schreiben

## 💰 Kosten

**Anthropic API Preise** (Stand 2024):

| Modell | Input | Output | 1000 Nachrichten ~|
|--------|--------|--------|-------------------|
| Haiku | $0.25/1M tokens | $1.25/1M tokens | **$2-5** |
| Sonnet | $3.00/1M tokens | $15.00/1M tokens | **$15-30** |
| Opus | $15.00/1M tokens | $75.00/1M tokens | **$50-100** |

**Tipp:** Starte mit Haiku für Tests, wechsle zu Sonnet für reguläre Nutzung.

## 🔄 Updates

Das Addon updated automatisch über Home Assistant:

1. **Benachrichtigung** erscheint bei neuer Version
2. **Add-ons** → **Claude Code** → **Update**
3. **Restart** erfolgt automatisch

## 🆘 Support

**Hilfe benötigt?**

- 📚 **Dokumentation**: Siehe [GitHub Wiki](https://github.com/DawidSu/ha-claude-code-addon/wiki)
- 🐛 **Bug Report**: [GitHub Issues](https://github.com/DawidSu/ha-claude-code-addon/issues)
- 💬 **Community**: [Home Assistant Community Forum](https://community.home-assistant.io)
- ✉️ **Kontakt**: GitHub [@DawidSu](https://github.com/DawidSu)

## 🤝 Beitragen

Beiträge sind willkommen! 

1. **Fork** das Repository
2. **Branch** erstellen: `git checkout -b feature/improvement`
3. **Änderungen** committen: `git commit -am 'Add improvement'`
4. **Push**: `git push origin feature/improvement`
5. **Pull Request** erstellen

## 📄 Lizenz

MIT License - siehe [LICENSE](LICENSE) Datei.

## 🙏 Danksagung

- **Anthropic** für die Claude API
- **Home Assistant** Community für die großartige Platform
- **Contributors** für Verbesserungen und Bug Reports

---

**Viel Spaß mit Claude Code in Home Assistant! 🚀**

> *Transformiere dein Smart Home mit der Power von Claude AI* 🤖✨