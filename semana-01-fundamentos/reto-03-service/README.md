# Reto 03 – Exponer la app con un Service ⭐⭐

## 🎯 Objetivo

Crear un **Service** que reparta el tráfico entre las réplicas del Deployment del reto 02 y probarlo desde dentro y desde fuera del clúster.

## 🧭 Repasa en el simulador

Flujo 2 – Tráfico, paso 4 (Service y kube-proxy: la grúa que reparte la carga).

## 📋 Antes de empezar

El Deployment `mi-app` del reto 02 debe estar corriendo:

```
kubectl get deployment mi-app
```

## 📋 Instrucciones

1. Completa `service.yaml`:
   - Nombre: `mi-app`.
   - El `selector` debe apuntar a los Pods con `app: mi-app`.
   - El Service escucha en el puerto `80` y envía al puerto `80` del contenedor.
2. Aplícalo:
   ```
   kubectl apply -f semana-01-fundamentos/reto-03-service/service.yaml
   ```
3. Revisa que el Service encontró los Pods (deben salir 3 IPs):
   ```
   kubectl get endpoints mi-app
   ```
4. Pruébalo **desde dentro** del clúster con un Pod temporal:
   ```
   kubectl run prueba --rm -it --image=busybox:1.36 --restart=Never -- wget -qO- http://mi-app
   ```
5. Pruébalo **desde tu PC**:
   ```
   kubectl port-forward service/mi-app 8080:80
   ```
   Abre http://localhost:8080.

## ✅ Cómo verificar

`kubectl get endpoints mi-app` muestra 3 direcciones IP y el paso 4 devuelve el HTML de nginx.

## 💡 Pista

Si `endpoints` sale vacío (`<none>`), el selector del Service no coincide con las etiquetas de los Pods. Compara con:

```
kubectl get pods --show-labels
```

## 🧠 Pregunta para la sesión

En el paso 4 usaste `http://mi-app` y no una IP. ¿Quién traduce ese nombre? (Pista: busca qué es CoreDNS).
