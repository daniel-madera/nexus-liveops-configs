# Nexus LiveOps Configs (GitOps Repository)

Repositorio de configuraciones desacopladas y esquemas de validación para **Nexus LiveOps Tool (Mattel / Project Wild)**.

## 📁 Estructura del Repositorio

* `schemas/`: Contratos de datos (JSON Schema + uiSchema). Son la **Single Source of Truth** que consume el `DynamicFormEngine` en Retool.
  * `schemas/offers/bundle_offer.json`: JSON Schema draft-07.
  * `schemas/offers/bundle_offer.ui.json`: Configuración de grid multi-columna para Retool.
* `configs/`: Configuraciones vivas del juego.
  * `configs/offers/summer_bundle.json`: Estado actual de la oferta.
* `.github/workflows/liveops-pipeline.yml`: Pipeline de CI/CD que valida los cambios con `ajv-cli` y emula la publicación a `staging` o `main`.

## 🌿 Estrategia de Ramas (GitOps Promotion)

1. **`staging`**: Recibe los cambios generados desde Retool para validación y testing de QA.
2. **`main`**: Producción. La promoción se realiza mediante un Pull Request aprobado por un Lead (aprobación dual).
