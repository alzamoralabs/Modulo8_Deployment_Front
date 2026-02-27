# Modulo8_Deployment_Front
# ⚔️ Kratos Motivational Agent — Frontend

Interfaz conversacional estilo ChatGPT construida con **Streamlit** para interactuar con el agente motivacional de Kratos. Diseño oscuro y atmosférico acorde a la personalidad del personaje.

> Este repositorio es el **frontend**. El backend vive en [Modulo8_Deployment](https://github.com/alzamoralabs/Modulo8_Deployment).

---

## 🖥️ Vista previa

```
⚔ KRATOS ⚔
Fantasma de Esparta · Dios de la Guerra · Padre de Atreus
─────────────────────────────────────────────────────────
                          [ No tengo fuerzas para seguir ]

⚔️  Muchacho. El cansancio no es el enemigo.
    La rendición sí lo es...
─────────────────────────────────────────────────────────
[ Habla. El Dios de la Guerra te escucha... ]
```

---

## 📁 Estructura del proyecto

```
Modulo8_Deployment_Front/
├── app.py               # Aplicación Streamlit
├── Dockerfile           # Imagen del frontend
├── docker-compose.yml   # Orquestación standalone
├── requirements.txt     # Dependencias Python
└── README.md
```

---

## ⚙️ Requisitos previos

- Python 3.11+
- El backend de Kratos corriendo (local o remoto)
- Docker Desktop (para ejecución containerizada)

---

## 🚀 Ejecución local (sin Docker)

```bash
# 1. Clonar el repositorio
git clone https://github.com/alzamoralabs/Modulo8_Deployment_Front.git
cd Modulo8_Deployment_Front

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Levantar (asegúrate que el backend esté corriendo en :8000)
streamlit run app.py
```

La app queda disponible en `http://localhost:8501`.

Si el backend corre en una URL distinta:

```bash
# Windows CMD
set KRATOS_API_URL=http://localhost:8000
streamlit run app.py

# Mac/Linux
KRATOS_API_URL=http://localhost:8000 streamlit run app.py
```

---

## 🐳 Ejecución con Docker

### 1. Configurar la URL del backend

```bash
cp .env.example .env
```

Edita el `.env`:

```env
# Si el backend corre en la misma máquina:
# Windows/Mac → host.docker.internal
# Linux       → 172.17.0.1
KRATOS_API_URL=http://host.docker.internal:8000
```

### 2. Levantar

```bash
docker compose up --build
```

Abre `http://localhost:8501` en el navegador.

---

## 🔧 Variables de entorno

| Variable | Requerida | Default | Descripción |
|---|---|---|---|
| `KRATOS_API_URL` | ✅ | `http://localhost:8000` | URL del backend de Kratos |

---

## 💬 Cómo usar la interfaz

La interfaz funciona igual que un chat:

1. Escribe tu mensaje en el campo inferior
2. Kratos responderá con la gravedad que merece cada pregunta
3. El historial de conversación se mantiene durante la sesión
4. El botón **LIMPIAR** reinicia la conversación

El campo `chat_history` se envía automáticamente al backend en cada mensaje para mantener el contexto de la conversación.

---

## 🔗 Repositorios relacionados

| Repo | Descripción |
|---|---|
| [Modulo8_Deployment](https://github.com/alzamoralabs/Modulo8_Deployment) | Backend — FastAPI + LangGraph + Amazon Bedrock |
| [Modulo8_Deployment_Front](https://github.com/alzamoralabs/Modulo8_Deployment_Front) | Frontend — Este repositorio |