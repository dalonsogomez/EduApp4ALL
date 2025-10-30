# EduApp4ALL

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-ISC-green.svg)
![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)
![React](https://img.shields.io/badge/react-18.3.1-blue.svg)

**Plataforma educativa gamificada para facilitar la integración de refugiados y migrantes**

EduApp4ALL es una plataforma educativa innovadora que combina gamificación con inteligencia artificial para ofrecer una experiencia de aprendizaje personalizada y multilingüe. Diseñada especialmente para apoyar la integración de refugiados y migrantes, la plataforma ofrece recursos educativos, seguimiento de progreso, y asistencia adaptativa con IA.

---

## Tabla de Contenidos

- [Características Principales](#características-principales)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Arquitectura del Sistema](#arquitectura-del-sistema)
- [Requisitos Previos](#requisitos-previos)
- [Instalación](#instalación)
  - [Opción 1: Instalación Rápida](#opción-1-instalación-rápida)
  - [Opción 2: Instalación Manual](#opción-2-instalación-manual)
  - [Opción 3: Docker Compose](#opción-3-docker-compose)
- [Configuración](#configuración)
- [Uso](#uso)
- [Scripts Disponibles](#scripts-disponibles)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Funcionalidades Detalladas](#funcionalidades-detalladas)
- [Testing](#testing)
- [Despliegue](#despliegue)
- [Solución de Problemas](#solución-de-problemas)
- [Contribuir](#contribuir)
- [Equipo](#equipo)
- [Licencia](#licencia)

---

## Características Principales

### Sistema de Gamificación Completo
- **Sistema XP y Niveles**: Progresión basada en puntos de experiencia con 50 niveles
- **Sistema de Insignias**: 14 insignias en 4 categorías (idiomas, cultura, habilidades blandas, logros)
- **Desafíos Diarios**: Nuevos retos cada día con recompensas especiales
- **Sistema de Rachas**: Mantén tu racha de días consecutivos jugando
- **Recompensas**: Monedas virtuales, vidas extra, multiplicadores de XP

### Inteligencia Artificial Avanzada
- **Asistente Educativo IA**: Tutor personalizado con Llama-3.1 o GPT-4
- **Reconocimiento de Voz**: Transcripción multilingüe con Whisper Large V3 (100+ idiomas)
- **Detección de Emociones**: Análisis de audio y texto para adaptar la dificultad
- **Feedback Personalizado**: Informes semanales con insights generados por IA
- **Ajuste Adaptativo**: Dificultad que se adapta según rendimiento y estado emocional

### Contenido Educativo
- **Juegos Educativos**: Múltiples categorías (idiomas, matemáticas, cultura, etc.)
- **Recursos Didácticos**: Biblioteca con documentos, videos, enlaces y cuestionarios
- **Multilingüe**: Soporte para más de 100 idiomas
- **Sensibilidad Cultural**: Contenido adaptado al contexto de refugiados y migrantes

### Seguimiento y Progreso
- **Dashboard Personalizado**: Vista general de progreso, XP, nivel y rachas
- **Historial de Juegos**: Registro completo de sesiones con estadísticas detalladas
- **Informes Semanales**: Análisis de rendimiento con recomendaciones de IA
- **Progreso de Insignias**: Seguimiento visual del avance hacia cada badge
- **Estadísticas Detalladas**: Precisión, tiempo jugado, categorías favoritas

### Perfil y Personalización
- **Perfiles de Usuario**: Información personal, intereses, nivel educativo
- **Avatar Personalizable**: Representación visual del usuario
- **Configuración de Privacidad**: Control sobre qué información compartir
- **Gestión de Cuenta**: Cambio de contraseña, notificaciones, preferencias

---

## Tecnologías Utilizadas

### Frontend
- **React 18.3.1**: Biblioteca de UI con hooks modernos
- **TypeScript**: Tipado estático para mayor seguridad
- **Vite**: Build tool ultra rápido
- **React Router 7**: Navegación SPA
- **TailwindCSS 3**: Framework CSS utility-first
- **Radix UI**: Componentes accesibles y personalizables
- **Recharts**: Gráficos y visualizaciones
- **Axios**: Cliente HTTP
- **React Hook Form + Zod**: Formularios con validación

### Backend
- **Node.js + Express**: Servidor HTTP
- **TypeScript**: Tipado en el backend
- **MongoDB + Mongoose**: Base de datos NoSQL
- **JWT**: Autenticación basada en tokens
- **Bcrypt**: Hash de contraseñas
- **Express Session**: Manejo de sesiones
- **Pino**: Logging estructurado

### Servicios de IA
- **Python 3.11**: Lenguaje para servicios de IA
- **FastAPI**: Framework web para APIs
- **LangChain**: Orquestación de agentes LLM
- **Transformers (HuggingFace)**: Modelos de ML
- **OpenAI Whisper**: Reconocimiento de voz
- **Llama 3.1**: Modelo de lenguaje
- **Wav2Vec2**: Detección de emociones en audio
- **DistilBERT**: Detección de emociones en texto

### DevOps y Herramientas
- **Docker + Docker Compose**: Containerización
- **Git**: Control de versiones
- **ESLint**: Linter para TypeScript/JavaScript
- **Concurrently**: Ejecución paralela de scripts
- **tsx**: Ejecución de TypeScript en Node.js

---

## Arquitectura del Sistema

```
┌─────────────────────────────────────────────────────────────┐
│                     EduApp4ALL                              │
└─────────────────────────────────────────────────────────────┘

┌──────────────────┐         ┌──────────────────┐         ┌──────────────────┐
│  React Frontend  │◄───────►│  Node.js Backend │◄───────►│   MongoDB        │
│   (Puerto 5173)  │         │   (Puerto 3000)  │         │  (Puerto 27017)  │
└──────────────────┘         └──────────────────┘         └──────────────────┘
        │                             │
        │                             │
        └─────────────┬───────────────┘
                      │
                      ▼
        ┌──────────────────────────┐
        │   AI Services (FastAPI)  │
        │      (Puerto 8001)       │
        └──────────────────────────┘
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
    ┌────────┐  ┌─────────┐  ┌──────────────┐
    │ Llama  │  │ Whisper │  │   Emotion    │
    │  LLM   │  │  (STT)  │  │  Detection   │
    └────────┘  └─────────┘  └──────────────┘
```

### Flujo de Datos
1. **Usuario** → Interactúa con la interfaz React
2. **Frontend** → Envía peticiones al backend Node.js
3. **Backend** → Gestiona autenticación, lógica de negocio y base de datos
4. **MongoDB** → Almacena usuarios, juegos, sesiones, recursos, etc.
5. **AI Services** → Procesa peticiones de IA (chat, transcripción, emociones)
6. **Modelos ML** → Generan respuestas inteligentes y adaptativas

---

## Requisitos Previos

### Software Requerido
- **Node.js**: >= 18.0.0 (recomendado 20.x)
- **npm**: >= 9.0.0 (viene con Node.js)
- **MongoDB**: >= 6.0 (local o Atlas)
- **Git**: >= 2.30

### Para Servicios de IA (Opcional)
- **Python**: >= 3.11
- **pip**: >= 23.0
- **CUDA**: >= 11.8 (para GPU, opcional)
- **16GB RAM**: Mínimo (32GB recomendado para IA)

### Tokens de API (Opcional)
- **HuggingFace Token**: Para modelos Llama (gratuito)
- **OpenAI API Key**: Para GPT-4 (de pago)
- **Anthropic API Key**: Para Claude (de pago)

---

## Instalación

### Opción 1: Instalación Rápida

Esta es la forma más rápida de iniciar el proyecto sin servicios de IA:

```bash
# 1. Clonar el repositorio
git clone https://github.com/dalonsogomez/EduApp4ALL.git
cd EduApp4ALL

# 2. Instalar todas las dependencias
npm install

# 3. Configurar variables de entorno
cp server/.env.example server/.env
# Edita server/.env con tu configuración de MongoDB

# 4. Inicializar base de datos con datos de ejemplo
npm run seed

# 5. Iniciar todos los servicios (frontend + backend)
npm run dev
```

Accede a la aplicación en: `http://localhost:5173`

### Opción 2: Instalación Manual

Para más control sobre cada componente:

#### 1. Clonar el Repositorio

```bash
git clone https://github.com/dalonsogomez/EduApp4ALL.git
cd EduApp4ALL
```

#### 2. Instalar Dependencias del Proyecto Compartido

```bash
cd shared
npm install
npm run build
cd ..
```

#### 3. Instalar Dependencias del Backend

```bash
cd server
npm install
cd ..
```

#### 4. Instalar Dependencias del Frontend

```bash
cd client
npm install
cd ..
```

#### 5. Configurar Variables de Entorno del Backend

Crea el archivo `server/.env`:

```bash
cd server
cp .env.example .env
```

Edita `server/.env` con tus valores:

```env
# Base de datos
MONGODB_URI=mongodb://localhost:27017/eduapp4all
# Para MongoDB Atlas:
# MONGODB_URI=mongodb+srv://usuario:password@cluster.mongodb.net/eduapp4all

# Servidor
PORT=3000
NODE_ENV=development

# Autenticación
JWT_SECRET=tu_secreto_super_seguro_cambialo
SESSION_SECRET=otro_secreto_para_sesiones

# AI Services (opcional)
AI_SERVICE_URL=http://localhost:8001
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
```

#### 6. Iniciar MongoDB

Si usas MongoDB local:

```bash
# Iniciar servicio de MongoDB
sudo systemctl start mongod

# O si lo instalaste manualmente:
mongod --dbpath /data/db
```

Si usas MongoDB Atlas, asegúrate de que `MONGODB_URI` apunte a tu cluster.

#### 7. Poblar Base de Datos (Seed)

```bash
cd server
npm run seed
cd ..
```

Esto creará:
- Usuarios de ejemplo
- Juegos educativos
- Insignias
- Recursos didácticos
- Desafíos diarios

#### 8. Iniciar la Aplicación

Desde la raíz del proyecto:

```bash
# Iniciar frontend + backend simultáneamente
npm run dev
```

O iniciar cada servicio por separado:

```bash
# Terminal 1: Backend
cd server
npm run dev

# Terminal 2: Frontend
cd client
npm run dev
```

#### 9. Configurar Servicios de IA (Opcional)

Para habilitar las funcionalidades de IA:

```bash
# 1. Crear entorno virtual de Python
cd ai-services
python3 -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Configurar variables de entorno
cp .env.example .env
# Edita .env con tus tokens

# 4. Iniciar servicio de IA
./start.sh
# O manualmente: uvicorn api.main:app --host 0.0.0.0 --port 8001 --reload
```

### Opción 3: Docker Compose

Para un despliegue completo con todos los servicios:

```bash
# 1. Clonar el repositorio
git clone https://github.com/dalonsogomez/EduApp4ALL.git
cd EduApp4ALL

# 2. Configurar variables de entorno
cp server/.env.example server/.env
cp ai-services/.env.example ai-services/.env

# 3. Iniciar todos los servicios con Docker
docker-compose up -d

# 4. Ver logs
docker-compose logs -f

# 5. Poblar la base de datos
docker-compose exec server npm run seed

# 6. Detener servicios
docker-compose down
```

Los servicios estarán disponibles en:
- Frontend: `http://localhost:5173`
- Backend API: `http://localhost:3000`
- AI Services: `http://localhost:8001`
- MongoDB: `localhost:27017`

---

## Configuración

### Variables de Entorno del Backend (`server/.env`)

```env
# ======================
# Base de Datos
# ======================
MONGODB_URI=mongodb://localhost:27017/eduapp4all

# ======================
# Servidor
# ======================
PORT=3000
NODE_ENV=development

# ======================
# Autenticación
# ======================
JWT_SECRET=tu_secreto_jwt_super_seguro
SESSION_SECRET=tu_secreto_de_sesion

# ======================
# AI Services (Opcional)
# ======================
AI_SERVICE_URL=http://localhost:8001

# API Keys para modelos cloud (opcional)
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...

# ======================
# Otros
# ======================
CORS_ORIGIN=http://localhost:5173
```

### Variables de Entorno de AI Services (`ai-services/.env`)

```env
# ======================
# Tokens de Modelos
# ======================
HUGGINGFACE_TOKEN=hf_...

# API Keys alternativas (opcional)
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...

# ======================
# Configuración de Modelos
# ======================
LLM_MODEL=meta-llama/Llama-3.1-8B-Instruct
WHISPER_MODEL=large-v3
EMOTION_MODEL_AUDIO=ehcalabres/wav2vec2-lg-xlsr-en-speech-emotion-recognition
EMOTION_MODEL_TEXT=bhadresh-savani/distilbert-base-uncased-emotion

# ======================
# Performance
# ======================
USE_GPU=true
MAX_WORKERS=4
CACHE_DIR=./models

# ======================
# API
# ======================
AI_SERVICE_PORT=8001
```

---

## Uso

### Acceso a la Aplicación

1. Abre tu navegador en `http://localhost:5173`
2. Regístrate con un nuevo usuario o usa uno de los usuarios de prueba:
   - Email: `demo@eduapp4all.com`
   - Password: `demo123`

### Flujo de Usuario

1. **Registro/Login**: Crea una cuenta o inicia sesión
2. **Dashboard**: Ve tu progreso, nivel, XP, rachas e insignias
3. **Juegos**: Navega por categorías y juega juegos educativos
4. **Recursos**: Accede a la biblioteca de materiales didácticos
5. **Desafíos**: Completa desafíos diarios para ganar recompensas extra
6. **Perfil**: Personaliza tu perfil y revisa tu historial
7. **Progreso**: Ve informes semanales con insights de IA

### Funcionalidades Principales

#### Jugar un Juego
```
1. Click en "Juegos" en el menú
2. Selecciona una categoría (Idiomas, Matemáticas, etc.)
3. Elige un juego
4. Completa las preguntas
5. Recibe feedback personalizado con IA
6. Gana XP, monedas y progresa en insignias
```

#### Ver Progreso Semanal
```
1. Click en "Progreso" en el menú
2. Ve tu informe semanal con:
   - Juegos completados
   - XP ganado
   - Precisión promedio
   - Gráfico de actividad diaria
   - Insights generados por IA
   - Fortalezas y áreas de mejora
```

#### Completar Desafíos Diarios
```
1. Click en "Desafíos" en el menú
2. Ve los 3 desafíos del día
3. Completa las tareas (jugar X juegos, ganar Y XP, etc.)
4. Recibe recompensas especiales
5. Los desafíos se renuevan cada día a medianoche
```

#### Usar el Asistente IA
```
1. Click en el icono de chat
2. Escribe tu pregunta en cualquier idioma
3. Recibe respuestas personalizadas del tutor IA
4. Usa el botón de micrófono para hablar (reconocimiento de voz)
```

---

## Scripts Disponibles

### Desde la Raíz del Proyecto

```bash
# Desarrollo - Iniciar todos los servicios
npm run dev

# Instalación - Instalar todas las dependencias
npm install

# Linting - Revisar código de todos los módulos
npm run lint

# Inicializar base de datos
npm run seed

# Limpiar base de datos
npm run cleanup-db        # Limpia progreso de usuarios
npm run cleanup-db:all    # Limpia todo excepto usuarios y juegos
npm run cleanup-db:full   # Limpia TODO (cuidado!)

# Debug - Iniciar con inspector de Node.js
npm run debug
```

### Backend (`cd server && npm run ...`)

```bash
npm run dev              # Iniciar en modo desarrollo (hot reload)
npm start               # Iniciar en modo producción
npm run build           # Compilar TypeScript
npm run lint            # Linter ESLint

# Base de datos
npm run seed            # Poblar base de datos con datos de ejemplo
npm run cleanup-db      # Limpiar progreso de usuarios
npm run cleanup-db:all  # Limpiar casi todo
npm run cleanup-db:full # Limpiar base de datos completa

# Testing
npm run test:profile           # Test de perfil de usuario
npm run test:game-session      # Test de sesiones de juego
npm run test:games-crud        # Test de CRUD de juegos
npm run test:progress          # Test de endpoints de progreso
npm run test:challenges        # Test de desafíos diarios
npm run test:rewards           # Test de sistema de recompensas
npm run test:resources         # Test de recursos educativos
npm run test:xp                # Test de sistema XP
npm run test:streak            # Test de sistema de rachas
npm run test:streak-expiration # Test de expiración de rachas

# Demos
npm run demo:resources  # Demo interactivo de recursos
npm run demo:streak     # Demo interactivo de rachas

# Utilidades
npm run manage-games    # Script para gestionar juegos
```

### Frontend (`cd client && npm run ...`)

```bash
npm run dev      # Iniciar en modo desarrollo (puerto 5173)
npm start        # Alias de dev
npm run build    # Build de producción
npm run preview  # Previsualizar build de producción
npm run lint     # Linter ESLint
```

### Shared (`cd shared && npm run ...`)

```bash
npm run build    # Compilar tipos compartidos
npm run dev      # Watch mode para desarrollo
npm run lint     # Linter ESLint
```

### AI Services (`cd ai-services && ...`)

```bash
./start.sh                           # Iniciar servicio de IA
python -m pytest tests/              # Ejecutar tests
uvicorn api.main:app --reload        # Iniciar con hot reload
python -m api.main                   # Iniciar directamente
```

---

## Estructura del Proyecto

```
EduApp4ALL/
├── client/                          # Frontend React
│   ├── src/
│   │   ├── api/                     # Clientes API
│   │   ├── components/              # Componentes reutilizables
│   │   ├── hooks/                   # Custom hooks
│   │   ├── pages/                   # Páginas/vistas
│   │   ├── contexts/                # React contexts
│   │   ├── lib/                     # Utilidades
│   │   └── App.tsx                  # Componente raíz
│   ├── public/                      # Archivos estáticos
│   ├── package.json
│   └── vite.config.ts               # Configuración Vite
│
├── server/                          # Backend Node.js
│   ├── server/                      # Servidor Express
│   │   ├── auth.ts                  # Middleware de autenticación
│   │   └── server.ts                # Punto de entrada
│   ├── routes/                      # Rutas API
│   │   ├── authRoutes.ts            # Autenticación
│   │   ├── gameRoutes.ts            # Juegos
│   │   ├── progressRoutes.ts        # Progreso
│   │   ├── challengeRoutes.ts       # Desafíos
│   │   ├── rewardRoutes.ts          # Recompensas
│   │   └── resourceRoutes.ts        # Recursos
│   ├── models/                      # Modelos Mongoose
│   │   ├── User.ts                  # Usuario
│   │   ├── Game.ts                  # Juego
│   │   ├── GameSession.ts           # Sesión de juego
│   │   ├── Badge.ts                 # Insignia
│   │   ├── Challenge.ts             # Desafío
│   │   ├── Reward.ts                # Recompensa
│   │   └── Resource.ts              # Recurso educativo
│   ├── services/                    # Lógica de negocio
│   │   ├── progressService.ts       # Servicio de progreso
│   │   ├── xpService.ts             # Sistema XP
│   │   ├── challengeService.ts      # Desafíos
│   │   ├── rewardService.ts         # Recompensas
│   │   ├── llmService.ts            # Integración LLM
│   │   └── aiClient.ts              # Cliente AI services
│   ├── scripts/                     # Scripts de utilidad
│   │   ├── seed.ts                  # Seed de base de datos
│   │   ├── cleanup-database.ts      # Limpiar base de datos
│   │   └── test-*.ts                # Scripts de testing
│   └── package.json
│
├── shared/                          # Código compartido
│   ├── types/                       # Tipos TypeScript compartidos
│   │   ├── user.ts
│   │   ├── game.ts
│   │   └── ...
│   ├── config/                      # Configuración compartida
│   └── package.json
│
├── ai-services/                     # Servicios de IA (Python)
│   ├── api/
│   │   └── main.py                  # FastAPI app
│   ├── services/
│   │   ├── llm_agent.py             # Agente educativo LLM
│   │   ├── speech_service.py        # Whisper STT
│   │   └── emotion_service.py       # Detección de emociones
│   ├── requirements.txt             # Dependencias Python
│   ├── start.sh                     # Script de inicio
│   └── .env                         # Configuración IA
│
├── docs/                            # Documentación
│   ├── AI_IMPLEMENTATION.md
│   ├── IMPLEMENTATION_SUMMARY.md
│   ├── PROGRESS_TRACKING_IMPLEMENTATION.md
│   ├── XP_IMPLEMENTATION_SUMMARY.md
│   └── ...
│
├── docker-compose.yml               # Orquestación Docker
├── package.json                     # Scripts raíz
└── README.md                        # Este archivo
```

---

## Funcionalidades Detalladas

### Sistema de XP y Niveles

- **50 Niveles**: Progresión desde nivel 1 hasta 50
- **XP Escalado**: Requisitos de XP aumentan por nivel (nivel 1 = 100 XP, nivel 50 = 5000 XP)
- **Fuentes de XP**:
  - Completar juegos (50-150 XP según dificultad)
  - Completar desafíos diarios (100-200 XP)
  - Mantener rachas consecutivas (bonus diario)
  - Ganar insignias (bonus único)

### Sistema de Insignias

14 insignias organizadas en 4 categorías:

#### Idiomas (3 insignias)
- Iniciado en Idiomas
- Políglota
- Maestro de Idiomas

#### Cultura (3 insignias)
- Explorador Cultural
- Conocedor Cultural
- Embajador Cultural

#### Habilidades Blandas (3 insignias)
- Aprendiz Colaborativo
- Líder de Equipo
- Mentor Comunitario

#### Logros (5 insignias)
- Primeros Pasos
- Jugador Dedicado
- Estudiante Comprometido
- Maestro del Aprendizaje
- Leyenda Educativa

Cada insignia tiene 5 niveles con requisitos crecientes de XP.

### Sistema de Desafíos Diarios

- **3 Desafíos Nuevos Cada Día**: Se renuevan a medianoche UTC
- **Tipos de Desafíos**:
  - Completar X juegos de una categoría
  - Ganar Y puntos de XP
  - Alcanzar Z% de precisión
  - Jugar juegos en diferentes categorías
- **Recompensas**: Monedas, vidas, multiplicadores de XP
- **Estado**: Activo, completado, expirado

### Sistema de Rachas

- **Racha Actual**: Días consecutivos jugando
- **Mejor Racha**: Récord personal
- **Bonus de Racha**:
  - 7 días: +50 XP bonus
  - 14 días: +100 XP bonus
  - 30 días: +200 XP bonus
- **Recordatorios**: Se pierde la racha si no juegas en 24h

### Sistema de Recompensas

- **Monedas**: Moneda virtual para desbloquear contenido
- **Vidas**: Intentos extra en juegos difíciles
- **Multiplicadores de XP**: 1.5x, 2x por tiempo limitado
- **Obtención**: Completar juegos, desafíos, logros

### Recursos Educativos

Biblioteca con 4 tipos de recursos:

1. **Documentos**: PDFs, artículos, guías
2. **Videos**: Tutoriales, lecciones grabadas
3. **Enlaces**: Sitios web externos útiles
4. **Cuestionarios**: Evaluaciones y tests

Organizados por:
- Categoría (idiomas, matemáticas, cultura, etc.)
- Nivel de dificultad (principiante, intermedio, avanzado)
- Idioma
- Tags/etiquetas

### Asistente IA

Funcionalidades del tutor inteligente:

- **Chat Multilingüe**: Conversa en 100+ idiomas
- **Personalización**: Adapta respuestas según edad, nivel, intereses
- **Feedback Pedagógico**: Análisis de rendimiento y sugerencias
- **Generación de Preguntas**: Crea ejercicios adaptativos
- **Recomendaciones**: Sugiere recursos y juegos según progreso
- **Detección de Emociones**: Ajusta tono y dificultad según estado emocional

### Reconocimiento de Voz

- **Transcripción**: Convierte audio a texto en 100+ idiomas
- **Traducción Automática**: Traduce a inglés si es necesario
- **Detección de Idioma**: Identifica el idioma hablado
- **Integración con Chat**: Habla con el asistente IA usando voz
- **Formatos Soportados**: WAV, MP3, M4A, OGG

---

## Testing

### Backend Tests

El proyecto incluye múltiples suites de pruebas:

```bash
cd server

# Probar todo el sistema de progreso
npm run test:progress

# Probar desafíos diarios
npm run test:challenges

# Probar sistema XP
npm run test:xp

# Probar sistema de rachas
npm run test:streak

# Probar sistema de recompensas
npm run test:rewards

# Probar recursos educativos
npm run test:resources
```

### AI Services Tests

```bash
cd ai-services

# Activar entorno virtual
source venv/bin/activate

# Ejecutar todos los tests
python -m pytest tests/ -v

# Test específico
python -m pytest tests/test_llm_agent.py -v
```

### Tests Manuales

Prueba los endpoints con curl:

```bash
# Health check del backend
curl http://localhost:3000/api/health

# Health check de AI services
curl http://localhost:8001/api/ai/health

# Login
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"demo@eduapp4all.com","password":"demo123"}'

# Obtener perfil (requiere token JWT)
curl http://localhost:3000/api/auth/profile \
  -H "Authorization: Bearer YOUR_JWT_TOKEN"
```

---

## Despliegue

### Despliegue en Producción

#### 1. Preparar Variables de Entorno

Configura las variables de entorno de producción en `server/.env`:

```env
NODE_ENV=production
MONGODB_URI=mongodb+srv://usuario:password@cluster.mongodb.net/eduapp4all
JWT_SECRET=secreto_super_seguro_generado_aleatoriamente
SESSION_SECRET=otro_secreto_aleatorio
CORS_ORIGIN=https://tu-dominio.com
```

#### 2. Build del Frontend

```bash
cd client
npm run build
# Los archivos compilados estarán en client/dist/
```

#### 3. Build del Backend

```bash
cd server
npm run build
# Los archivos compilados estarán en server/dist/
```

#### 4. Servir la Aplicación

Puedes usar varios enfoques:

**Opción A: Servir frontend y backend desde Express**

Configura Express para servir los archivos estáticos del frontend:

```typescript
// En server/server.ts
import path from 'path';
import { fileURLToPath } from 'url';

const __dirname = path.dirname(fileURLToPath(import.meta.url));

app.use(express.static(path.join(__dirname, '../../client/dist')));

app.get('*', (req, res) => {
  res.sendFile(path.join(__dirname, '../../client/dist/index.html'));
});
```

**Opción B: Usar Nginx como reverse proxy**

Configura Nginx para servir el frontend y proxy al backend:

```nginx
server {
    listen 80;
    server_name tu-dominio.com;

    # Frontend
    location / {
        root /var/www/eduapp4all/client/dist;
        try_files $uri $uri/ /index.html;
    }

    # Backend API
    location /api {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

#### 5. Configurar Process Manager

Usa PM2 para mantener el backend corriendo:

```bash
# Instalar PM2 globalmente
npm install -g pm2

# Iniciar backend
cd server
pm2 start dist/server/server.js --name eduapp4all-backend

# Ver logs
pm2 logs eduapp4all-backend

# Reiniciar
pm2 restart eduapp4all-backend

# Configurar inicio automático
pm2 startup
pm2 save
```

#### 6. Desplegar AI Services (Opcional)

Para servicios de IA en producción:

```bash
cd ai-services

# Instalar dependencias
pip install -r requirements.txt

# Iniciar con Gunicorn (production ASGI server)
gunicorn api.main:app \
  --workers 4 \
  --worker-class uvicorn.workers.UvicornWorker \
  --bind 0.0.0.0:8001 \
  --timeout 120 \
  --daemon

# O usar systemd service
sudo systemctl start eduapp4all-ai
```

### Despliegue con Docker

Producción simplificada con Docker:

```bash
# 1. Build de imágenes
docker-compose -f docker-compose.prod.yml build

# 2. Iniciar servicios
docker-compose -f docker-compose.prod.yml up -d

# 3. Monitoreo
docker-compose -f docker-compose.prod.yml logs -f

# 4. Escalar servicios
docker-compose -f docker-compose.prod.yml up -d --scale server=3
```

### Plataformas Cloud Recomendadas

#### Vercel (Frontend)
- Deploy automático desde GitHub
- Edge network global
- SSL gratis

#### Railway (Backend + MongoDB)
- Despliegue fácil con Git
- MongoDB integrado
- Escalado automático

#### Render (Fullstack)
- Soporte Docker
- Base de datos PostgreSQL/MongoDB
- SSL y CDN incluidos

#### AWS (Producción Escalable)
- EC2 para backend
- S3 + CloudFront para frontend
- DocumentDB para MongoDB
- Elastic Load Balancer

---

## Solución de Problemas

### El frontend no se conecta al backend

**Problema**: `Network Error` o `CORS Error`

**Solución**:
1. Verifica que el backend esté corriendo: `curl http://localhost:3000/api/health`
2. Revisa la configuración de CORS en `server/server.ts`
3. Confirma que `CORS_ORIGIN` en `.env` coincida con la URL del frontend
4. Revisa la consola del navegador para errores específicos

### MongoDB no conecta

**Problema**: `MongoNetworkError` o `Connection refused`

**Solución**:
1. Verifica que MongoDB esté corriendo: `sudo systemctl status mongod`
2. Confirma que `MONGODB_URI` en `.env` sea correcta
3. Si usas Atlas, revisa que tu IP esté en la lista blanca
4. Prueba la conexión: `mongosh "tu_mongodb_uri"`

### Servicios de IA no cargan los modelos

**Problema**: `Out of memory` o `Model not found`

**Solución**:
1. Usa modelos más ligeros (Llama-1B en vez de 8B)
2. Cierra otras aplicaciones que consuman RAM
3. Verifica que `HUGGINGFACE_TOKEN` sea válido
4. Cambia `LLM_MODEL=openai` para usar API en vez de local
5. Aumenta memoria disponible o usa instancia con más RAM

### Las peticiones de IA son muy lentas

**Problema**: Transcripción/Chat tarda más de 30 segundos

**Solución**:
1. **GPU**: Asegúrate de tener CUDA instalado y `USE_GPU=true`
2. **Modelos**: Usa versiones más pequeñas (Whisper `medium` o `small`)
3. **Quantización**: Habilita 8-bit quantization en `llm_agent.py`
4. **API Externa**: Cambia a OpenAI/Anthropic API para mayor velocidad
5. **Instancia**: Usa una instancia con GPU (AWS p3, GCP GPU, etc.)

### Error al ejecutar seed

**Problema**: `npm run seed` falla con errores de duplicados

**Solución**:
1. Limpia la base de datos primero: `npm run cleanup-db:full`
2. Luego ejecuta seed de nuevo: `npm run seed`
3. Si persiste, verifica conexión a MongoDB

### El build de TypeScript falla

**Problema**: `tsc` muestra errores de tipos

**Solución**:
1. Asegúrate de tener las dependencias de `shared` instaladas y compiladas:
   ```bash
   cd shared
   npm install
   npm run build
   ```
2. Limpia y reinstala dependencias:
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```
3. Verifica que las versiones de TypeScript coincidan en todos los módulos

### Los tests fallan

**Problema**: `npm run test:*` muestra errores

**Solución**:
1. Asegúrate de que el backend esté corriendo
2. Ejecuta seed antes de los tests: `npm run seed`
3. Verifica que MongoDB esté accesible
4. Revisa que no haya conflictos de puertos

### Problemas con autenticación

**Problema**: No puedo hacer login o el token expira

**Solución**:
1. Verifica que `JWT_SECRET` esté configurado en `.env`
2. Limpia cookies/localStorage del navegador
3. Revisa que el token no haya expirado (por defecto 7 días)
4. Confirma que el usuario exista en la base de datos

---

## Contribuir

¡Contribuciones son bienvenidas! Si quieres colaborar con EduApp4ALL:

### Proceso de Contribución

1. **Fork** el repositorio
2. **Crea una rama** para tu feature (`git checkout -b feature/AmazingFeature`)
3. **Commit** tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. **Push** a la rama (`git push origin feature/AmazingFeature`)
5. Abre un **Pull Request**

### Guía de Estilo

- Usa TypeScript con tipado estricto
- Sigue las convenciones de ESLint configuradas
- Escribe comentarios claros y concisos
- Añade tests para nuevas funcionalidades
- Actualiza la documentación si es necesario

### Áreas de Contribución

- Nuevos juegos educativos
- Traducciones a más idiomas
- Mejoras en la UI/UX
- Optimizaciones de rendimiento
- Corrección de bugs
- Documentación
- Tests

### Reportar Bugs

Usa GitHub Issues para reportar bugs. Incluye:

- Descripción clara del problema
- Pasos para reproducir
- Comportamiento esperado vs actual
- Screenshots si aplica
- Entorno (OS, versiones de Node/npm, etc.)

---

## Equipo

EduApp4ALL fue desarrollado por:

- **Borja De La Torre Bokobza** - Full Stack Developer
- **Daniel Alonso Gómez** - Backend & AI Engineer
- **María Paula Beltrán Herrera** - Frontend & UX Designer
- **Kunyi Huang** - Data Science & ML Engineer

### Proyecto

Desarrollado para **Hack4Edu 2025** - Hackathon enfocado en soluciones educativas para poblaciones vulnerables.

### Contacto

- **GitHub**: [https://github.com/dalonsogomez/EduApp4ALL](https://github.com/dalonsogomez/EduApp4ALL)
- **Email**: contacto@eduapp4all.com (próximamente)

---

## Licencia

Este proyecto está bajo la Licencia ISC. Ver el archivo `LICENSE` para más detalles.

---

## Agradecimientos

- **HuggingFace** por proporcionar acceso a modelos open-source
- **MongoDB** por la base de datos
- **Anthropic** y **OpenAI** por las APIs de LLM
- **Comunidad Open Source** por las increíbles herramientas utilizadas
- **Hack4Edu** por la oportunidad de crear impacto social

---

## Roadmap

### Q1 2025
- [ ] Despliegue en producción
- [ ] App móvil (React Native)
- [ ] Integración con plataformas educativas
- [ ] Modo offline

### Q2 2025
- [ ] Más juegos y recursos educativos
- [ ] Sistema de clases virtuales
- [ ] Comunidad y foros
- [ ] Certificaciones y badges oficiales

### Q3 2025
- [ ] Fine-tuning de modelos para contexto de refugiados
- [ ] Partnerships con ONGs
- [ ] Expansión a más regiones
- [ ] Análisis avanzado de learning analytics

---

**¿Preguntas? ¿Sugerencias?** Abre un issue en GitHub o contacta al equipo.

¡Gracias por usar EduApp4ALL! Juntos facilitamos la integración y educación para todos.
