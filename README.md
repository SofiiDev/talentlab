# TalentLab — Portal de Empleos Ciencia & Tecnología

Hosting: GitHub Pages (gratis) | Base de datos: Supabase (gratis)

---

## Setup en 10 minutos

### 1. Supabase — Crear la base de datos

1. Ir a supabase.com → New project
2. Elegir nombre (ej: "talentlab") y contraseña
3. Ir a **SQL Editor** → New query
4. Pegar y ejecutar el contenido de `supabase-setup.sql`
5. Ir a **Settings → API** y copiar:
   - Project URL → `https://xxxx.supabase.co`
   - anon/public key
   - service_role key (solo para admin.html)
6. Ir a **Storage** → New bucket:
   - Nombre: `avatars`
   - Public: ✅ sí
7. Ir a **Authentication → URL Configuration**:
   - Site URL: `https://TU-USUARIO.github.io/talentlab`
   - Redirect URLs: agregar la misma URL

### 2. Configurar las credenciales en los HTML

En `index.html` y `admin.html`, reemplazar:
```js
const SUPABASE_URL  = 'https://TU_PROYECTO.supabase.co';
const SUPABASE_ANON = 'TU_ANON_KEY';
```

Solo en `admin.html`, también reemplazar:
```js
const SUPABASE_SERVICE = 'TU_SERVICE_ROLE_KEY';
```
⚠️ La service role key solo va en admin.html, NUNCA en index.html

### 3. Crear usuario admin en Supabase

1. Supabase → Authentication → Users → Invite user
2. Ingresá el email que usarás para el admin
3. Con ese email te logueás en admin.html

### 4. Deploy en GitHub Pages

1. Crear repo en GitHub (ej: `talentlab`)
2. Subir los archivos (index.html, admin.html, supabase-setup.sql, README.md)
3. Settings → Pages → Source: Deploy from branch → main → / (root)
4. URL: `https://TU-USUARIO.github.io/talentlab`

---

## Credenciales admin

El panel admin usa **autenticación de Supabase** — el login verifica contra
los usuarios de Authentication → Users de Supabase.

Para crear el primer admin:
Supabase → Authentication → Users → Invite user → ingresá tu email

---

## Estructura

```
├── index.html          Portal de candidatos
├── admin.html          Panel de administración
├── supabase-setup.sql  Script SQL para crear las tablas
└── README.md
```

## Tablas en Supabase

| Tabla        | Contenido                          |
|--------------|------------------------------------|
| profiles     | Perfiles de candidatos              |
| jobs         | Avisos publicados por TalentLab     |
| applications | Postulaciones de candidatos         |

## Storage en Supabase

Bucket `avatars` — fotos de perfil de los candidatos
