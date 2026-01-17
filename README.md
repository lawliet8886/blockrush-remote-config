# BlockRush Remote Config

Este repositório hospeda o arquivo `remote_config.json` usado pelo app para:
- balanceamento (combo, daily, boss)
- live ops (eventos por data)
- feature flags (liga/desliga modos)
- A/B test simples (offline bucket)

## Regras
- NÃO colocar segredos aqui (tokens, chaves, credenciais).
- Sempre que mudar balance importante, aumente `version`.
- Datas usam `yyyyMMdd` (ex: 20260117).

## Campos principais

### version / minSupportedVersion
- `version`: aumenta quando fizer mudanças relevantes
- `minSupportedVersion`: se o app estiver abaixo disso, ignora config

### features
- enableDaily: habilita Daily Rift
- enableOverlord: habilita Overlord Encounter
- cleanHudDefault: default do HUD clean
- interstitialEnabled: deve ficar false por padrão
- devPanelEnabled: painel dev (recomendado true em testes)

### balance
- dailyBaseTarget: alvo base do Daily
- dailyStreakStep: quanto aumenta por dia de streak
- comboGain / comboDecay: tuning do meter (0..1)
- bossEveryClears: frequência do boss no modo Overlord (ou gatilho)
- bossCriticalAlsoTriggers: se CRITICAL também pode chamar boss

### drops
- tokenDaily: tokens ao completar Daily
- tokenBoss: tokens ao vencer boss
- tokenPerfectChance: chance de token em Perfect Clear (0..1)
- crateCommonChance: chance de drop cosmético common
- riftWChance + riftWClearsStep: chance e gatilho do W no Daily (se você usar isso)

## Eventos
Em `events`, cada evento tem:
- id
- startKey / endKey
- mutationOverride (opcional)
- coinMultiplier (opcional)
- bossFreqOverride (opcional)

## A/B tests
Em `ab.experiments`, cada experimento tem variantes com `weight` e `overrides`.
Overrides são strings do tipo:
- "balance.comboGain": "0.26"
