# ☸️ Fundamentos de Kubernetes

Curso práctico y comunitario para aprender Kubernetes desde cero: entender qué pasa dentro del clúster y resolver retos reales cada semana.

## 🧭 Simulador interactivo

Antes de cada sesión, recorre el simulador. Muestra paso a paso qué hace cada componente del clúster, con una analogía de un puerto de contenedores:

👉 **[Abrir el simulador](https://juanesjm1610.github.io/fundamentos-kubernetes/simulador.html)**

Tiene 4 flujos:
1. **Despliegue** – de `kubectl apply` a un Pod `Running`.
2. **Tráfico** – cómo llega una petición del usuario hasta tu Pod.
3. **Auto-curación** – qué hace Kubernetes cuando un Pod se cae.
4. **Diagnóstico** – retos de Pods rotos para practicar troubleshooting.

## 📅 Sesiones

| Día | Hora (Colombia) | Modalidad |
|---|---|---|
| Martes | 6:00 – 8:00 p. m. | Virtual (Zoom) |
| Jueves | 6:00 – 8:00 p. m. | Virtual (Zoom) |

**Registro:** _(pon aquí el enlace de tu comunidad)_. Te registras en cada evento y te llega el enlace de la sesión.

## 🛠️ Requisitos

- [Git](https://git-scm.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [kind](https://kind.sigs.k8s.io/) (Kubernetes local dentro de Docker)
- Un editor, por ejemplo [VS Code](https://code.visualstudio.com/)

En Windows puedes instalarlos con `winget`:

```
winget install --id Git.Git -e
```
```
winget install --id Docker.DockerDesktop -e
```
```
winget install --id Kubernetes.kubectl -e
```
```
winget install --id Kubernetes.kind -e
```

## 🚀 Cómo trabajar los retos

1. Haz **fork** de este repositorio (botón *Fork* arriba a la derecha).
2. Clona **tu** fork:
   ```
   git clone https://github.com/TU-USUARIO/fundamentos-kubernetes.git
   ```
3. Entra a la carpeta:
   ```
   cd fundamentos-kubernetes
   ```
4. Conecta el repo original para recibir los retos nuevos:
   ```
   git remote add upstream https://github.com/Juanesjm1610/fundamentos-kubernetes.git
   ```
5. Crea tu clúster local (con Docker Desktop abierto):
   ```
   kind create cluster --name curso
   ```
6. Resuelve los retos y sube tus soluciones a tu fork:
   ```
   git add .
   ```
   ```
   git commit -m "Solución reto 01"
   ```
   ```
   git push origin main
   ```
7. Cada semana trae los retos nuevos:
   ```
   git pull upstream main
   ```

## 📚 Contenido

| Semana | Tema | Retos |
|---|---|---|
| [01](semana-01-fundamentos/) | Pods, Deployments, Services y diagnóstico | 4 |
| 02 | ConfigMaps, Secrets y volúmenes | Próximamente |
| 03 | Ingress y redes | Próximamente |
| 04 | Probes, recursos y escalado | Próximamente |

## 🤝 Comunidad

¿Dudas? Abre un *Issue* en este repositorio o pregunta en la sesión en vivo.
