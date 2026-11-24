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
| Direcciones GitHub catalogadas | **328** (medido con el mismo regex en un solo barrido: 275 preexistentes + 53 nuevas) |
| Nuevas este pass (2º del día) | **53 → 53 live, 0 dead** vía `git ls-remote` |
| Base preexistente re-auditada | 275 slugs → **272 live / 3 dead**, y los 3 son exactamente los que este KB ya publica como muertos (**0 nuevas direcciones muertas**) |
| Patterns componibles | **P1–P33** |
| Tendencias registradas | **N1–N29** |
| Licencias verificadas | byte-read desde `raw.githubusercontent.com`, con la **rama por defecto resuelta vía `git ls-remote --symref HEAD`** |

## 🔌 Segundo pass del 2026-11-24 — plano de la interfaz de carga (OCPP / OCPI / ISO 15118)

Plano **virgen**: `OCPP`, `OCPI`, `EVerest`, `SteVe` y `charging station` tenían **0 menciones** en los
9 archivos. No se reescribió el primer pass del día (00:56Z); se verificó y se abrió terreno nuevo.

| Hallazgo | Detalle |
|---|---|
| **Asimetría 765×** | La capa de protocolo es enorme y permisiva (`evcc-io/evcc` MIT **7.654★**); el agente del lado operador **no existe**: `charging station agent license:apache-2.0` = **0**. Los 9 servidores MCP reales son todos *driver-side*, mediana 1★. |
| **Especificación obligatoria sin licencia** | **23 CFR 680.108** exige conformidad con **OCPI 2.2.1**; `ocpi/ocpi` (602★) **no tiene archivo de licencia en 36 rutas** y su sucesor está detrás de la membresía de la EV Roaming Foundation. |
| **Dos trampas de licencia nuevas** | `dsV2Gshark` (115★): **MIT y GPL-2.0 repartidos por directorio** — el entregable es la parte GPL. `ChargePoint/wireshark-v2g` (65★): **licencia por referencia** a `openv2g` → LGPL-3.0, rama `trunk`. |
| **Defecto propio corregido antes de publicar** | El §13 de GPL-3.0 **contiene** «GNU Affero General Public License», así que un detector que busca `AFFERO` primero etiqueta GPL-3.0 como AGPL-3.0. Afectó a 4 repos, incluido **SteVe**. Regla nueva: anclar en el **título** de la licencia, nunca en el cuerpo. |
| **Rama por defecto versionada** | `ocpi/ocpi` apunta a **`2.3.0/release/core`**; `master` sigue devolviendo 200 con texto **superado**. Segunda observación de esta clase en la red de KBs. |
| **LATAM es la región con el caso más duro, al revés de lo habitual** | Chile: **DS 12 + Pliego Técnico 15 exigen OCPP 1.6 o superior** por nombre, con instructivo **Res. Ex. N°41458 (2026)** y plataforma de registro. Único país LATAM con entregable de cumplimiento cotizable hoy. |
| **Brecha declarada** | **Brasil: 0 resultados** sobre regulación de interoperabilidad de carga; APAC sin equivalente a NEVI y sin fuente primaria china. Registrado como *no establecido*, no como ausencia. |

**Correcciones publicadas en el primer pass del día** — dos afirmaciones previas de este KB quedaron refutadas por
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
