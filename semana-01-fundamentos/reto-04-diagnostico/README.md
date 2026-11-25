# Reto 04 – El puerto está roto (diagnóstico) ⭐⭐⭐

## 🎯 Objetivo

Alguien desplegó una app llamada `tienda` y **no funciona**. Tu trabajo es encontrar y corregir **3 errores** escondidos en `roto.yaml`, usando solo `get`, `describe`, `logs` y `endpoints`.

> ⚠️ No leas el YAML buscando el error a simple vista. La idea es practicar el diagnóstico con kubectl, como en la vida real.

## 🧭 Repasa en el simulador

Flujo 4 – Diagnóstico (Retos Rotos). Abre los retos ImagePullBackOff, Pending y Sin endpoints.

## 📋 Instrucciones

1. Despliega la app rota:
   ```
   kubectl apply -f semana-01-fundamentos/reto-04-diagnostico/roto.yaml
   ```
2. Mira el estado:
   ```
   kubectl get pods -l app=tienda
   ```
3. Para cada síntoma, investiga:
   ```
   kubectl describe pod NOMBRE-DEL-POD
   ```
   ```
   kubectl get endpoints tienda
   ```
   ```
   kubectl get events --sort-by=.lastTimestamp
   ```
4. Corrige `roto.yaml` y vuelve a aplicarlo cuantas veces necesites.
5. Anota cada error en la tabla de abajo.

## 📝 Tu bitácora de diagnóstico

| # | Síntoma que viste | Comando que te dio la pista | Causa | Cómo lo corregiste |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

## ✅ Cómo verificar

- `kubectl get pods -l app=tienda` muestra **2/2 Pods `Running`**.
- `kubectl get endpoints tienda` muestra **2 IPs**.
- Esto devuelve el HTML de nginx:
  ```
  kubectl run prueba --rm -it --image=busybox:1.36 --restart=Never -- wget -qO- http://tienda
  ```

> Los errores aparecen de a uno: cuando arreglas uno, sale el siguiente. Igual que en producción.

## 💡 Pistas (ábrelas solo si te atascas)

<details>
<summary>Pista 1</summary>

Si ves `ErrImagePull` o `ImagePullBackOff`, revisa en Events qué imagen intenta descargar. ¿Existe ese tag?
</details>

<details>
<summary>Pista 2</summary>

Si un Pod se queda en `Pending`, Events dirá algo como *Insufficient memory*. ¿Cuánta memoria está pidiendo?
</details>

<details>
<summary>Pista 3</summary>

Si los Pods están bien pero el Service no tiene endpoints, compara el selector del Service con `kubectl get pods --show-labels`.
</details>

## 🧹 Limpieza

```
kubectl delete -f semana-01-fundamentos/reto-04-diagnostico/roto.yaml
```
