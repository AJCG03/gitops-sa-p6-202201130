# Secretos y continuidad

Este directorio no contiene valores secretos. Los secretos actuales de `sa-p6` son creados fuera de Git y consumidos por los Rollouts mediante `secretKeyRef`.

Antes de una reconstruccion:

1. Confirmar que existe un backup Velero `Completed` que incluya el namespace `sa-p6`.
2. Restaurar el backup en un namespace de verificacion.
3. Verificar solo la existencia de las claves requeridas, sin imprimir valores.
4. Promover la restauracion despues de documentar el resultado.

La instalacion actual no tiene Sealed Secrets ni External Secrets Operator. Para cumplir una estrategia criptografica permanente, migrar estos secretos a GCP Secret Manager y desplegar External Secrets con Workload Identity. No subir JSON de cuentas de servicio, secretos Kubernetes, contrasenas ni archivos desencriptados.
