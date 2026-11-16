# CoWork Loop – Banca y finanzas

Hackathon de IA y Robótica Bangkok 2026 · Pista: Futuro del trabajo.

Aplicación web donde la IA (Gemini) decide si cada tarea de back-office bancario la hace un **robot** (rutinaria) o el **analista** (criterio), con una escena 3D y métricas en vivo. Español e inglés.

## Estructura
```
server.js        servidor Express (guarda la clave y llama a Gemini)
package.json
public/index.html  aplicación (interfaz + escena 3D)
.env.example     variables de entorno de ejemplo
```

## Probar en tu PC
```bash
npm install
# PowerShell:  $env:GEMINI_API_KEY="tu_clave"; npm start
# Mac/Linux:   GEMINI_API_KEY=tu_clave npm start
```
Abre http://localhost:3000. Sin clave, la app funciona con un clasificador por reglas.

## Desplegar en Render (Web Service)
1. Sube esta carpeta al repositorio de GitHub (nunca subas `.env` ni tu clave).
2. En Render: **New → Web Service**, conecta el repositorio.
3. Runtime **Node**. Build Command: `npm install`. Start Command: `node server.js`.
4. En **Environment** agrega `GEMINI_API_KEY` (tu clave de Google AI Studio) y, si quieres, `GEMINI_MODEL`.
5. **Create Web Service**. Verifica `https://TU-SITIO.onrender.com/api/health`: debe decir `"ai": true`.

En el plan gratuito el servicio se duerme tras un rato sin visitas; ábrelo antes de presentar.

## Seguridad
- La clave solo vive en el servidor (variable de entorno).
- Límite de 30 solicitudes por minuto por IP y tareas de máximo 300 caracteres.
- Las decisiones sensibles (fraude, AML, aprobar crédito) siempre se asignan al analista.
