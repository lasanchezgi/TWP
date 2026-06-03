# The War Project

Análisis empírico de los ciclos retóricos pre-bélicos de EE.UU. en Oriente Medio (1991–2026), usando datos del [GDELT Project 2.0](https://www.gdeltproject.org/) para documentar el patrón de cuatro fases que precede a cada intervención militar.

---

## El problema

Las guerras no empiezan cuando los primeros misiles cruzan una frontera. Empiezan semanas o meses antes, en los titulares, en los discursos presidenciales, en los medios que amplifican amenazas reales o inventadas. Este proyecto pregunta: ¿es ese proceso sistemático? ¿Tiene una estructura reconocible? ¿Es medible con datos?

**Hipótesis central:** las intervenciones militares de EE.UU. en Oriente Medio entre 1991 y 2026 son instancias de un mismo patrón retórico de cuatro fases, y ese patrón se ha ido comprimiendo históricamente.

---

## Casos analizados

| Caso | Tipo de ciclo | Fuente de datos |
| --- | --- | --- |
| Golfo 1991 | Construcción | GDELT real (v1) |
| Afganistán 2001 | Redirección | GDELT real (v1) |
| Irak 2003 | Fabricación | GDELT real (v1) |
| Libia 2011 | Construcción | Mock (API sin cobertura) |
| Irán 2026 | Fabricación | GDELT real (v2) |

### Tipos de ciclo

- **Construcción** — amenaza real o verificable, amplificada gradualmente. EGI bajo.
- **Redirección** — evento detonante real; el origen es suprimido y el objetivo de la respuesta es desviado (caso: Arabia Saudita → Afganistán en 26 días). RI: 0.5 → 1.0.
- **Fabricación** — las afirmaciones sobre la amenaza exceden sistemáticamente la evidencia verificable. EGI > 0.35 sostenido.

### Las cuatro fases del ciclo

| Fase | Ventana | Descripción |
| --- | --- | --- |
| I. Construcción del enemigo | D-180 a D-45 | La imagen del adversario como amenaza existencial |
| II. Justificación moral | D-45 a D-14 | El marco ético para la acción militar |
| III. Manufactura del consenso | D-14 a D-3 | Coalición doméstica e internacional |
| IV. Escalamiento | D-3 a D-0 | Cuenta regresiva pública hacia el ataque |

---

## Métricas

### Evidence Gap Index (EGI)

Mide la brecha entre la intensidad de las afirmaciones y la evidencia verificable:

```text
EGI(t) = claim_intensity(t) − evidence_score(t)
```

Umbral de fabricación: EGI > 0.35 durante 30+ días consecutivos.

### Redirection Index (RI)

Mide el desplazamiento del foco narrativo del origen al target redirigido:

```text
RI(t) = target_mentions(t) / (target_mentions(t) + suppressed_mentions(t))
```

RI → 1.0 indica supresión completa del origen.

---

## Estructura del repositorio

```text
the_war_project/
├── data/
│   └── gdelt_mock_v3.parquet   # Fallback simulado (reproducible sin conexión)
├── docs/
│   └── article.md              # Artículo de divulgación con hallazgos
├── img/                        # Gráficas exportadas por los notebooks
├── notebooks/
│   ├── 01_ciclo_retorico.ipynb     # Intensidad narrativa, aceleración y tono mediático
│   ├── 02_fabricacion_egi.ipynb    # Evidence Gap Index — Iraq 2003 e Irán 2026
│   ├── 03_redireccion.ipynb        # Fases, zoom Irán 2026 y Redirection Index
│   └── war_narratives_gdelt_v3.ipynb  # Notebook master (referencia completa)
├── requirements.txt
├── LICENCE
└── README.md
```

---

## Puesta en marcha

### 1. Clonar el repositorio

```bash
git clone <URL_DEL_REPO>
cd the_war_project
```

### 2. Crear entorno virtual e instalar dependencias

```bash
python -m venv .venv
source .venv/bin/activate       # macOS / Linux
# .venv\Scripts\activate        # Windows

pip install -r requirements.txt
```

### 3. Ejecutar los notebooks

```bash
jupyter notebook notebooks/
```

Los notebooks descargan datos GDELT en vivo si hay conexión. Si el API falla para algún caso, hacen fallback automático al parquet mock en `data/`. Libia 2011 siempre usa mock (el API no devuelve cobertura para ese período).

> **Nota:** La descarga de GDELT puede tardar varios minutos por caso, especialmente en v1 (datos pre-2015 con muestreo semanal).

---

## Principales hallazgos

- El ciclo retórico moderno **no escala gradualmente**: opera con base baja y un pico repentino concentrado en los últimos días antes de la invasión. Solo Golfo 1991 cruzó el umbral de alta intensidad con anticipación (D-39).
- **Irán 2026** es el único caso con tono mediático persistentemente negativo (AvgTone ≈ -4), la señal más robusta disponible en datos reales GDELT.
- El ciclo de Afganistán 2001 completó la redirección narrativa (Arabia Saudita → Afganistán) en **26 días**, con RI pasando de 0.689 a 0.860 el día de la invasión.
- El proxy EGI basado en códigos CAMEO tiene limitaciones: no distingue "evidencia que valida una amenaza" de "actividad diplomática paralela". El EGI operacional requiere NLP sobre el corpus de noticias.

---

## Stack

| Capa | Herramienta |
| --- | --- |
| Datos | GDELT Project 2.0 (`gdelt` v0.1.14) |
| Procesamiento | `pandas`, `numpy` |
| Visualización | `matplotlib`, `seaborn` |
| Notebooks | `jupyter`, `ipykernel` |
| Serialización | `pyarrow` (Parquet) |

---

## Artículo

El análisis completo, con todas las gráficas y contexto histórico, está disponible en [`docs/article.md`](docs/article.md).

---

## Licencia

MIT — consultar [LICENCE](LICENCE).

---

## Contacto

Laura Alejandra Sánchez Giraldo

[📧](mailto:laurasanchezgiraldo@outlook.es)
