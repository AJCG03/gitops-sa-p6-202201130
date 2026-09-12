# GitOps Repo — SA Platform P8

Repositorio **independiente** de manifiestos declarativos para el ecosistema de microservicios de la Práctica 8.

## Principio

Este repo es la **única fuente de verdad** del estado del clúster. Ningún pipeline aplica cambios directamente: el pipeline solo abre un Pull Request actualizando tags de imagen, y **ArgoCD** es el único componente que sincroniza contra Kubernetes.

## Estructura
.
├── apps/ # Applications de ArgoCD (una por microservicio)
├── rollouts/ # Rollouts canary (reemplazan a los Deployment)
├── analysis/ # AnalysisTemplates (smoke, integración, carga)
├── charts/ # Helm chart con valores por ambiente
│ └── sa-platform/
├── policies/ # Políticas Kyverno (mínimo 3)
└── secrets/ # SealedSecrets (nada en texto plano)
## Ambientes

- `dev`
- `staging`
- `prod`

## Convenciones

- **Prohibido** el tag `latest` en cualquier imagen.
- **Prohibido** secretos en texto plano. Todo va cifrado con Sealed Secrets.
- Los tags de imagen provienen de **tags de Git** (versionamiento semántico).
- Todos los `Deployment` fueron reemplazados por `Rollout` de Argo Rollouts.

## Enlaces

- Repo de código: privado (`Practicas-SA-B-202201130`)
- Cluster: GKE `practica6-cluster` (us-central1)
- Namespace: `sa-p6`
