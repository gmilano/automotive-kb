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
| Direcciones GitHub catalogadas | **378** (medido con un solo barrido regex sobre los 9 archivos: 331 preexistentes + **47 nuevas** este pass) |
| Nuevas este pass (3º del día) | **47 → 47 live, 0 dead** vía `git ls-remote` |
| Patterns componibles | **P1–P36** |
| Tendencias registradas | **N1–N33** |
| Licencias verificadas | byte-read desde `raw.githubusercontent.com`, con la **rama por defecto resuelta vía `git ls-remote --symref HEAD`**; control: un slug inventado devuelve DEAD |

## 🔗 Tercer pass del 2026-11-24 — plano de **data spaces** de la cadena de suministro (Catena-X / Tractus-X / EDC / AAS)

Plano **virgen**: `Catena-X`, `Tractus-X`, `dataspace`, `data space`, `battery passport`, `Lanelet2`,
`intrusion detection` e `insurance telematics` tenían **0 menciones** en los 9 archivos. No se reescribió
ningún pass anterior del día; se abrió terreno nuevo y es la capa **más permisiva** medida hasta ahora en
este KB (Apache-2.0 / MIT casi en su totalidad).

| Hallazgo | Detalle |
|---|---|
| 🔴 **El conector «community edition» más estrellado NO es open source** | `sovity/edc-ce` (96★, primer resultado de `topic:catena-x`): su `LICENSE` de **439 B** *nombra* Apache-2.0 pero fija **Elastic License 2.0 como default del repositorio**. Prohíbe ofrecer el software a terceros como servicio gestionado → **exclusión dura** para despliegue alojado por Globant. Usar `eclipse-tractusx/tractusx-edc` (Apache-2.0). |
| 🔴 **Regla nueva para toda la red de KBs** | **Comparar el tamaño del archivo de licencia con la longitud canónica de la licencia que nombra.** Medido aquí: Apache-2.0 = **10.141–11.559 B**, GPL-3.0 ≈ 35.148 B, AGPL-3.0 ≈ 34.522 B, CC-BY-4.0 ≈ 16.677–18.655 B, MIT ≈ 1.024–1.086 B, MIT-0 = 945 B, BSD-3 = 1.476 B. **Un archivo <2 KB que nombra Apache/GPL/MPL/EPL es un puntero, no una concesión** — hay que leerlo como prosa. Primer caso en este KB donde `NOASSERTION` era la respuesta honesta y el byte-read el engañoso. |
| ✅ **Las fechas del AI Act ya son afirmables** | **Digital Omnibus = Reg. (UE) 2026/1744**, DOUE **24-jul-2026**, vigor **27-jul-2026**. Anexo I productos embebidos — **donde están los vehículos** — **2-ago-2028**; Anexo III 2-dic-2027; sandboxes 2-ago-2027; **Art. 50 transparencia aplica desde 2-ago-2026, NO se aplazó**. Los **requisitos no cambiaron**: sólo las fechas de exigibilidad. Cierra 4 passes de «fechas en disputa». |
| ✅ **EMEA gana una ventanilla con fecha** | **Tractus-X Accelerator**: fase de implementación desde **1-sep-2026**, dura **2026–2029**, financia el **BMWE** alemán; socios ARENA2036, Catena-X Automotive Network, Fraunhofer ISST, IDSA. Dirigido a **PyMEs y mid-caps aún no activas en Catena-X**; **solicitudes cierran a fin de diciembre de 2026** → ver **P36**. |
| 🗓 **Fecha dura no-AV para toda la cadena** | **Pasaporte de batería obligatorio el 18-feb-2027** (Art. 77, Reg. (UE) 2023/1542) para baterías de VE, LMT e industriales **>2 kWh**. Obliga al **operador que coloca la batería en el mercado de la UE**; **sin retroactividad**; contenido inicial delgado → fase 1 a precio fijo, fase 2 retainer (**P34**). |
| 🔴 **Un mandato legal con esquema obligatorio y sin implementación licenciada — 2ª vez** | `batterypass/BatteryPassDataModel` (**70★, el modelo de datos más estrellado**) **no tiene archivo de licencia**; `open-dpp/open-dpp` (35★) es **AGPL-3.0**; el único base limpio, `eclipse-tractusx/digital-product-pass` (Apache-2.0), **no recibe push desde 2025-09-18**. Misma forma que OCPI en el 2º pass. |
| 📊 **Plataforma madura, agentes inexistentes** | `org:eclipse-tractusx` = **83 repos** medidos, releases trimestrales (`R26.06`). Pero `catena-x agent` devuelve **4 repos en total** y la **mediana del tier de agentes es 3★**. La decisión de plataforma está cerrada; **el trabajo diferenciado es el agente** → *adoptar la plataforma, construir el agente*. |
| 🆕 **La brecha del mapa, cerrada: era vocabulario, no suministro** | `fzi-forschungszentrum-informatik/Lanelet2` (**979★, BSD-3-Clause**) — el formato de mapa HD que **consume Autoware**. El KB tenía Autoware desde el ciclo 2 y `HD map` en 11 líneas de prosa, pero **`Lanelet2` con 0 menciones**: se buscó la *categoría*, nunca el *nombre del artefacto*. |
| 🔴 **Dos brechas cerradas con motivo, no con conteo** | **UBI / telemática de seguros: no existe anchor open source** — los primeros resultados son el SDK **propietario de Damoov** (`Mobile-Telematics/*`, 76★, «Damoov Service Terms»). **IDS de CAN: exactamente 1 repo permisivo licenciado** (12★). R155 exige detección → **cotizar como desarrollo propio o licencia comercial, nunca como «sobre open source»**. |
| ✅ **La regla de consultas cortas se confirma por 3ª vez** | `manufacturing quality inspection license:apache-2.0` (4 términos) = **2 repos**; `anomaly detection license:apache-2.0` (3 términos) = **1.525**, encabezado por **anomalib (6.420★)**. Escribir el cero de 4 términos habría **publicado una brecha fabricada**. |
| 🌎 **LATAM: primera ley de IA de la región y un número de fragmentación** | **Perú aprobó la primera ley de IA**; Colombia emitió circulares de principios; Brasil y Chile se esperan. **Universidad de los Andes (2026): 716 instrumentos regulatorios de IA en 23 países y territorios** → el entregable es un **mapa de aplicabilidad jurisdiccional**. **Stellantis y Toyota comprometieron AEB en autos nuevos ensamblados en Brasil para 2027**. El pasaporte de batería llega a LATAM como **obligación de exportación heredada del cliente europeo** (**P34/P35** + **P8** USMCA = misma plomería vendida dos veces). |

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
