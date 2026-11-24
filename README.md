---
industry: automotive
region: Global
updated: 2026-11-24
---

# 🚗 Automotive KB

> Knowledge base de la industria **Automotive** para Globant AI Studios.
> Connected vehicles, predictive maintenance, dealer agents, EV ecosistema

## Estado (2026-11-24)

| Métrica | Valor |
|---|---|
| Direcciones GitHub catalogadas | **277** |
| Nuevas este pass | 47 (47 live, 0 dead vía `git ls-remote`) |
| Patterns componibles | **P1–P30** |
| Tendencias registradas | **N1–N23** |
| Licencias verificadas | byte-read desde `raw.githubusercontent.com` |

**Correcciones publicadas este pass** — dos afirmaciones previas de este KB quedaron refutadas por
medición y fueron retiradas: (1) *"la capa V2X/C-ITS no tiene ningún anchor permisivo"* es **falsa**
(`ika-rwth-aachen/etsi_its_messages` es MIT); (2) *"cero repos de origen LATAM"* era un artefacto de
**buscar sólo en inglés** (`automotriz` → 2.458 repos; el problema real es que **95 de los primeros 100
no tienen licencia alguna**). Detalle en `agents/trending.md` y `repos/trending.md`.

**Brecha cerrada:** regulación APAC — ahora con texto normativo fechado (China **GB 44721-2026**,
vigente 1-jul-2027; **GB 47955-2026**, vigente 1-ene-2027).

## Estructura

```
automotive-kb/
├── agents/        # Agentes AI open source de la industria
├── repos/         # Repos MIT/Apache como punto de partida
├── verticals/     # Plataformas verticales customizables con AI
├── intel/         # Mercado, players, tendencias
├── compose/       # Recetas: cómo componer soluciones
└── ingest/        # Scripts de actualización automática
```

## Uso

1. **Nuevo engagement**: leer `intel/market.md` + `repos/foundations.md`
2. **Proponer solución AI**: `agents/top.md` + `compose/patterns.md`
3. **Mantenerse al día**: correr `ingest/update.sh` semanalmente

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
