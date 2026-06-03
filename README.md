# The War Project

Proyecto de análisis de datos orientado a explorar, limpiar, transformar y visualizar información relacionada con conflicto/war data en un flujo reproducible.

---

## 📌 Descripción

Este repositorio contiene un flujo de trabajo de *data lab* para:

- Ingestar datos crudos.
- Preparar y normalizar fuentes.
- Construir análisis exploratorio (EDA).
- Generar resultados y artefactos reutilizables.

La meta es facilitar análisis consistentes y trazables para investigación, reportes o experimentación analítica.

---

## 🎯 Objetivos

- Centralizar datos y transformaciones en un solo proyecto.
- Garantizar reproducibilidad de resultados.
- Hacer explícitos los supuestos de limpieza y modelado.
- Facilitar colaboración entre perfiles técnicos y no técnicos.

---

## 🗂️ Estructura sugerida del proyecto

```bash
the_war_project/
├── data/
│   ├── raw/            # Datos originales (sin modificar)
│   ├── interim/        # Transformaciones intermedias
│   └── processed/      # Datos listos para análisis/modelado
├── notebooks/          # Exploración y prototipos
├── src/                # Código fuente reutilizable
│   ├── ingest/         # Carga de datos
│   ├── cleaning/       # Limpieza y validación
│   ├── features/       # Ingeniería de variables
│   └── visualization/  # Gráficas y reporting
├── reports/            # Resultados, figuras, salidas
├── tests/              # Pruebas automáticas
├── requirements.txt    # Dependencias Python (si aplica)
└── README.md
```

---

## ⚙️ Requisitos

- Python 3.10+ (recomendado)
- `pip` o `poetry` para gestión de dependencias
- Jupyter (opcional, para notebooks)

---

## 🚀 Puesta en marcha

### 1) Clonar repositorio

```bash
git clone <URL_DEL_REPO>
cd the_war_project
```

### 2) Crear y activar entorno virtual

```bash
python -m venv .venv
source .venv/bin/activate    # macOS/Linux
# .venv\Scripts\activate     # Windows PowerShell
```

### 3) Instalar dependencias

```bash
pip install -r requirements.txt
```

---

## 🧪 Flujo de trabajo recomendado

1. **Ingesta:** colocar fuentes en `data/raw/`.
2. **Limpieza:** ejecutar scripts/notebooks de limpieza hacia `data/interim/`.
3. **Procesamiento:** generar datasets finales en `data/processed/`.
4. **Análisis:** correr notebooks o scripts en `src/`.
5. **Reporte:** exportar tablas/figuras en `reports/`.

---

## ✅ Buenas prácticas

- No modificar directamente datos en `data/raw/`.
- Versionar únicamente artefactos relevantes.
- Documentar cambios metodológicos importantes.
- Mantener funciones reutilizables en `src/` y no solo en notebooks.
- Añadir pruebas para transformaciones críticas.

---

## 🔐 Ética y uso responsable

Si el proyecto usa datos sensibles o geopolíticos:

- Evitar exposición de información personal.
- Citar y respetar licencias de las fuentes.
- Explicitar limitaciones y sesgos de datos.

---

## 🧾 Licencia

Este proyecto se distribuye bajo la licencia MIT.

Puedes consultar el texto completo en el archivo [LICENCE](LICENCE).

---

## 📬 Contacto

**Laura Sánchez** — AI Engineer

[📧](mailto:laurasanchezgiraldo@outlook.es)

¿Ideas, datos o escalas que quieras sumar? ¡Conversemos!
