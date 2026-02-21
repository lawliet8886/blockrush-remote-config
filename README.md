# 📤 Arquivos para GitHub

Esta pasta contém os arquivos que devem ser colocados no repositório GitHub do remote config.

## 📁 Arquivo: `remote_config.json`

### Onde colocar no GitHub:
```
https://github.com/lawliet8886/blockrush-remote-config/blob/main/remote_config.json
```

### Como atualizar:
1. Acesse o repositório GitHub `blockrush-remote-config`
2. Clique no arquivo `remote_config.json`
3. Clique no ícone de lápis (Edit)
4. Substitua TODO o conteúdo pelo que está nesta pasta
5. Clique em "Commit changes"

### ⚠️ Importante:
- **Os dois arquivos devem ser IGUAIS:**
  - `Paragithub/remote_config.json` (aqui)
  - `app/src/main/assets/remote_config_default.json` (no projeto)
  
- **Sempre aumente a `version`** quando fizer mudanças!
  - Versão atual: **5**
  
- **O app busca atualizações a cada 12 horas**

---

## 🎉 Eventos Incluídos (2026)

| Data | Evento | Bônus |
|------|--------|-------|
| 29 Jan - 12 Feb | 🐴 Lunar New Year | 2x coins |
| 10-16 Feb | 💕 Valentine's Rush | 1.5x coins |
| 13-18 Feb | 🎭 Carnival Chaos | 1.75x coins |
| 14-20 Mar | 🍀 Lucky Blocks | 1.5x coins |
| 01 Apr | 🃏 April Fools Mayhem | 2x coins |
| 03-07 Apr | 🐰 Easter Egg Hunt | 1.5x coins |
| 22-24 Apr | 🌍 Earth Day | 1.5x coins |
| 05-07 May | 🌮 Cinco de Mayo | 1.75x coins |
| 20-26 Jun | ☀️ Summer Solstice | 1.5x coins |
| 04-06 Jul | 🎆 Fireworks Festival | 2x coins |
| 15-31 Jul | 🏖️ Beach Party | 1.25x coins |
| 25-31 Aug | 📚 Back to School | 1.5x coins |
| 19 Sep - 04 Oct | 🍺 Oktoberfest | 1.5x coins |
| 25-31 Oct | 🎃 Spooky Season | 2x coins + Boss Rush |
| 01-02 Nov | 💀 Día de los Muertos | 2x coins |
| 26-29 Nov | 🦃 Thanksgiving | 1.75x coins |
| 27-30 Nov | 🛒 Black Friday | 1.5x coins + Shop Sale |
| 20-31 Dec | ❄️ Winter Wonderland | 2x coins + Daily Gifts |
| 31 Dec - 01 Jan | 🎉 New Year's Countdown | 3x coins! |

### Eventos de Fim de Semana (Rotativos)
- 👾 Boss Rush Weekend
- ⚡ Combo Challenge
- 🏃 Speed Run Showdown
- ✨ Perfect Clear Party
- ❓ Mystery Monday

---

## 🔧 Como Adicionar Novo Evento

Adicione um objeto na lista `events`:

```json
{
  "id": "event_nome_unico",
  "startKey": "YYYYMMDD",
  "endKey": "YYYYMMDD",
  "name": "🎮 Nome do Evento",
  "description": "Descrição divertida!",
  "category": "seasonal",
  "palette": { "primary": "#COR1", "accent": "#COR2", "glow": "#COR3" },
  "coinMultiplier": 1.5,
  "bossFreqOverride": 10
}
```

### Campos opcionais:
- `bossFreqOverride`: Frequência de boss (menor = mais frequente)
- `mutationOverride`: Modificador especial de gameplay
- `category`: "seasonal", "weekend", "flash"


## ✅ app-ads.txt (AdMob)

Arquivo publicado:
- `app-ads.txt` (raiz do repositório)
- `docs/app-ads.txt` (publicado via GitHub Pages)

URL correta para este repositório (`blockrush-remote-config`):
- `https://lawliet8886.github.io/blockrush-remote-config/app-ads.txt`

> `https://lawliet8886.github.io/app-ads.txt` só funciona se o repositório for exatamente `lawliet8886.github.io`.

### Se der 404, confira:
- Se você estiver trabalhando na branch `work`, o deploy também é disparado (workflow configurado para `main` e `work`).
1. **Pages habilitado** em `Settings > Pages`.
2. Fonte configurada para **GitHub Actions** (workflow `Deploy GitHub Pages`).
3. Arquivo existe no deploy em `docs/app-ads.txt`.
4. O deploy da action terminou com sucesso em `Actions`.
5. Aguarde 2-10 minutos após o primeiro deploy.
