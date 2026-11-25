# Semana 01 – Fundamentos: Pods, Deployments y Services

## 🎯 Qué vas a aprender

- Qué es un Pod y cómo se crea.
- Por qué casi nunca se crean Pods sueltos y se usan Deployments.
- Cómo Kubernetes se repara solo (auto-curación).
- Cómo exponer tu aplicación con un Service.
- Los 3 comandos para diagnosticar casi cualquier problema: `get`, `describe` y `logs`.

## 🧭 Antes de empezar

Recorre en el [simulador](https://juanesjm1610.github.io/fundamentos-kubernetes/simulador.html):
- **Flujo 1 – Despliegue** (para los retos 01 y 02).
- **Flujo 3 – Auto-curación** (para el reto 02).
- **Flujo 2 – Tráfico** (para el reto 03).
- **Flujo 4 – Diagnóstico** (para el reto 04).

Verifica que tu clúster esté arriba:

```
kubectl get nodes
```

Debes ver `curso-control-plane` en estado `Ready`. Si no existe:

```
kind create cluster --name curso
```

## 🧩 Retos

| # | Reto | Dificultad |
|---|---|---|
| 01 | [Mi primer Pod](reto-01-primer-pod/) | ⭐ |
| 02 | [Deployment y auto-curación](reto-02-deployment/) | ⭐⭐ |
| 03 | [Exponer la app con un Service](reto-03-service/) | ⭐⭐ |
| 04 | [El puerto está roto (diagnóstico)](reto-04-diagnostico/) | ⭐⭐⭐ |

## 📝 Chuleta de la semana

| Comando | Para qué sirve |
|---|---|
| `kubectl apply -f archivo.yaml` | Crear o actualizar recursos |
| `kubectl get pods -o wide` | Ver Pods, su nodo y su IP |
| `kubectl describe pod NOMBRE` | Ver detalle y eventos (¡aquí están los errores!) |
| `kubectl logs NOMBRE` | Ver lo que imprime la aplicación |
| `kubectl delete -f archivo.yaml` | Borrar lo que creó el archivo |
| `kubectl get events --sort-by=.lastTimestamp` | Ver la historia reciente del clúster |

## 🧹 Al terminar la semana

```
kubectl delete all --all
```
