# Reto 01 – Mi primer Pod ⭐

## 🎯 Objetivo

Crear tu primer Pod con un servidor web `nginx` y comprobar que está corriendo.

## 🧭 Repasa en el simulador

Flujo 1 – Despliegue, pasos 1 a 8. Fíjate en cómo el Pod pasa de `Pending` a `ContainerCreating` y luego a `Running`.

## 📋 Instrucciones

1. Abre el archivo `pod.yaml` de esta carpeta. Le faltan 3 datos marcados con `# TODO`.
2. Complétalo para que:
   - El Pod se llame `mi-primer-pod`.
   - Tenga la etiqueta `app: web`.
   - Use la imagen `nginx:1.27`.
3. Aplícalo:
   ```
   kubectl apply -f semana-01-fundamentos/reto-01-primer-pod/pod.yaml
   ```
4. Míralo cambiar de estado:
   ```
   kubectl get pods -w
   ```
   (Sal con `Ctrl + C`).
5. Entra a la aplicación desde tu navegador. Abre una conexión temporal:
   ```
   kubectl port-forward pod/mi-primer-pod 8080:80
   ```
   Abre http://localhost:8080. Deberías ver *Welcome to nginx!*

## ✅ Cómo verificar

```
kubectl get pod mi-primer-pod
```

Debe decir `1/1` y `Running`.

## 💡 Pista

Si el Pod no sale de `ContainerCreating` o muestra un error, ejecuta:

```
kubectl describe pod mi-primer-pod
```

y lee la sección **Events** al final.

## 🧠 Pregunta para la sesión

Borra el Pod con `kubectl delete pod mi-primer-pod`. ¿Volvió a aparecer solo? ¿Por qué no? (La respuesta está en el reto 02).
