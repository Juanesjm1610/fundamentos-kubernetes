# Reto 02 – Deployment y auto-curación ⭐⭐

## 🎯 Objetivo

Desplegar tu app con un **Deployment** de 3 réplicas, comprobar que Kubernetes repone los Pods que se caen y escalar la app.

## 🧭 Repasa en el simulador

- Flujo 1 – Despliegue, paso 4 (Controller Manager crea el ReplicaSet).
- Flujo 3 – Auto-curación completo.

## 📋 Instrucciones

1. Completa `deployment.yaml` (busca los `# TODO`):
   - 3 réplicas.
   - El `selector` debe coincidir con las etiquetas del template (`app: mi-app`).
2. Aplícalo:
   ```
   kubectl apply -f semana-01-fundamentos/reto-02-deployment/deployment.yaml
   ```
3. Revisa los 3 niveles que se crearon:
   ```
   kubectl get deploy,rs,pods
   ```
4. **Auto-curación:** abre una segunda terminal y déjala observando:
   ```
   kubectl get pods -w
   ```
   En la primera terminal, borra uno de los Pods (copia un nombre de la lista):
   ```
   kubectl delete pod NOMBRE-DEL-POD
   ```
   Observa en la segunda terminal cómo aparece un Pod nuevo.
5. **Escala** a 5 réplicas:
   ```
   kubectl scale deployment mi-app --replicas=5
   ```
6. Vuelve a 3 editando el YAML (cambia `replicas`) y aplicando otra vez. Esa es la forma recomendada: el archivo es la fuente de verdad.

## ✅ Cómo verificar

```
kubectl get deployment mi-app
```

Debe mostrar `READY 3/3`.

## 💡 Pista

Si aparece el error *selector does not match template labels*, revisa que `spec.selector.matchLabels` y `spec.template.metadata.labels` tengan exactamente lo mismo.

## 🧠 Pregunta para la sesión

¿Quién repuso el Pod borrado: el Deployment, el ReplicaSet o el kubelet? Justifícalo con lo que viste en el simulador.
