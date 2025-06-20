# 🌱 Clima-MundoVerde

Clima-MundoVerde es una API REST desarrollada en TypeScript y Express que permite consultar datos climáticos en tiempo real desde OpenWeather API. Los resultados se almacenan en Supabase (PostgreSQL) para fines de auditoría y análisis posteriores.

## 📦 Tecnologías Utilizadas

- Node.js + Express
- TypeScript
- TypeORM
- Supabase (PostgreSQL gestionado)
- OpenWeather API
- Axios
- Dotenv
- CORS
- JWT (para autenticación)
- Jest + Supertest (para testing)

## 🔧 Requisitos Previos

- Node.js ≥ 18.x
- Docker Compose
- Cuenta gratuita en OpenWeatherMap (para obtener una API key)

## 🚀 Instalación y Ejecución

### Clonar el repositorio
```bash
git clone https://github.com/EZMayk/MundoVerde.git
cd MundoVerde
```

### Instalación de dependencias
```bash
npm install
```

### Configuración del entorno
Crea un archivo `.env` en la raíz del proyecto con el siguiente contenido:
```env
DB_HOST=aws-0-us-east-2.pooler.supabase.com
DB_PORT=6543
DB_USERNAME=postgres.xsdzrbphlibhwmegavsc
DB_PASSWORD=Menendez2025*_*
DB_DATABASE=postgres
PORT=3000
OPENWEATHER_API_KEY=fbf0bedef7d799633876a3253f1e575a
OPENWEATHER_BASE_URL=https://api.openweathermap.org/data/2.5/weather
```

### Instalación de JWT
```bash
npm install jsonwebtoken
npm install --save-dev @types/jsonwebtoken
```

### Instalación de Jest para pruebas
```bash
npm install --save-dev jest ts-jest @types/jest supertest @types/supertest
```
### incia la configuracion de jest
```
npx ts-jest config:init
```

### instalacion de supertest para simular peticiones HTTP a tu servidor Express para los test de routes.
```bash
npm install --save-dev supertest @types/supertest
```

### Ejecución del proyecto
```bash
npm run dev
```
El servidor estará disponible en: `http://localhost:3000`

## 📂 Estructura Principal del Proyecto
```text
├── src/
│   ├── config/
│   ├── controllers/
│   ├── dtos/
│   ├── entities/
│   ├── middlewares/
│   ├── repositories/
│   ├── routes/
│   ├── services/
│   ├── test/
│   ├── utils/
│   ├── app.ts
├── tests/
├── .env
├── .gitignore
├── docker-compose.yml
├── package-lock.json
├── package.json
├── README.MD
└── tsconfig.json
```

## 📡 Endpoints Disponibles

### Consultar Clima Actual
- **Método:** GET  
- **URL:** `/api/consulta-clima?ciudad=Guayaquil`

#### Parámetros:
- `ciudad` (string) → Nombre de la ciudad a consultar.

✔️ Este endpoint:
- Consulta la API de OpenWeather.
- Guarda los datos en Supabase.
- Registra la consulta en la base de datos.
- Almacena un log de la consulta.

### Obtener Fuentes Climáticas
- **Método:** GET  
- **URL:** `/api/fuentes`

### Obtener Logs de Consultas
- **Método:** GET  
- **URL:** `/api/logs`

#### Parámetros opcionales:
- `ciudad` → Filtra por ciudad.
- `resultado` → Filtra por "éxito" o "error".
- `fuente` → Filtra por fuente climática.

#### Ejemplo sin filtros:
```http
GET http://localhost:3000/api/logs
```

#### Ejemplo con filtros:
```http
GET http://localhost:3000/api/logs?ciudad=Quito&resultado=éxito
```

## ✅ Pruebas Unitarias y de Integración
Para ejecutar las pruebas:
```bash
npm test
```

## 📜 Scripts disponibles en package.json
```json
"scripts": {
  "dev": "nodemon --exec ts-node src/app.ts",
  "start": "ts-node-dev src/app.ts",
  "test": "jest"
}
```
