# 🤖 Agente Global `.agents` - TallerMecanico

## 📌 Descripción General

El agente `.agents` es un **sistema de automatización centralizado** para el desarrollo y mantenimiento de la aplicación **TallerMecanico** en Flutter. Proporciona guías, scripts y mejores prácticas para todo el ciclo de desarrollo.

---

## 🎯 Propósito del Agente

- ✅ **Automatizar** setup y configuración
- ✅ **Estandarizar** procesos de desarrollo
- ✅ **Documentar** arquitectura y flujos
- ✅ **Facilitar** colaboración en equipo
- ✅ **Acelerar** implementación de features

---

## 🛠️ Skills Disponibles

### 1️⃣ Design Skill (🎨)
**Crear interfaces visuales y componentes**

Cubre:
- Diseño de pantallas
- Componentes reutilizables
- Paleta de colores
- Tipografía y spacing
- Responsividad

Archivos: `design-skill.md`

---

### 2️⃣ Code Skill (💻)
**Implementar funcionalidades y lógica de negocio**

Cubre:
- Modelos de datos
- Servicios (Firestore, Auth)
- State Management (Provider)
- CRUD Operations
- Testing

Archivos: `code-skill.md`

---

### 3️⃣ Workflow Skill (🔄)
**Orquestar procesos y flujos de datos**

Cubre:
- Flujos CRUD detallados
- Navegación
- Sincronización en tiempo real
- Manejo de errores
- Ciclo de vida de entidades

Archivos: `workflow-skill.md`

---

### 4️⃣ Planner Skill (⏱️)
**Automatizar tareas, testing y deployment**

Cubre:
- Scripts de automatización
- Verificación de dependencias
- Setup de Firebase
- CI/CD Pipeline
- Deployment strategies

Archivos: `planner-skill.md`

---

## 📁 Estructura del Agente

```
.agents/
├── SKILL.md                     ← Este archivo
│
├── skills/
│   ├── design-skill.md          ← Skill de diseño UI
│   ├── code-skill.md            ← Skill de código backend
│   ├── workflow-skill.md        ← Skill de flujo de trabajo
│   └── planner-skill.md         ← Skill planificador
│
├── scripts/
│   ├── verify-dependencies.sh   ← Verificar herramientas
│   ├── setup-firebase.sh        ← Configurar Firebase
│   └── init-project.sh          ← Inicializar proyecto
│
└── resources/
    └── firebase-setup.md        ← Guía Firebase paso a paso
```

---

## ✅ Prerequisitos

### Herramientas Requeridas

#### Flutter (v3.0+)
```bash
flutter --version
# Flutter 3.x.x-stable
```

#### Dart (v2.17+)
```bash
dart --version
# Dart 2.17.x (stable)
```

#### Firebase CLI
```bash
firebase --version
# Firebase CLI 12.0.0
```

#### Android SDK
```bash
flutter doctor
# [✓] Android toolchain - develop for Android devices
```

#### Visual Studio Code (Recomendado)
- Extension: Flutter
- Extension: Dart
- Extension: Firebase
- Extension: Pubspec Assist

---

## 🚀 Quick Start

### Paso 1: Verificar Ambiente
```bash
bash .agents/scripts/verify-dependencies.sh
```

**Resultado esperado:**
```
Flutter: Flutter 3.x.x-stable
Dart: Dart 2.17.x (stable)
Firebase: Firebase CLI 12.x.x
✅ Todas las herramientas están OK
```

---

### Paso 2: Configurar Firebase
```bash
bash .agents/scripts/setup-firebase.sh
```

**Pasos:**
1. Crear proyecto en Firebase Console
2. Agregar app Android
3. Descargar `google-services.json`
4. Copiar a `android/app/`
5. Crear Firestore Database

---

### Paso 3: Inicializar Proyecto
```bash
bash .agents/scripts/init-project.sh
```

**Resultado:**
```
📦 flutter pub get...
✅ Proyecto inicializado
```

---

### Paso 4: Ejecutar Aplicación
```bash
flutter run
```

**En emulador/dispositivo:**
- ✅ TallerMecanico app inicia
- ✅ HomeScreen visible
- ✅ Tabs: Automóviles, Servicios

---

## 📊 Flujo de Desarrollo

```
┌─────────────────────────────────────┐
│  1. Design Skill                    │
│  ├─ Crear wireframes                │
│  ├─ Diseñar pantallas               │
│  └─ Definir componentes             │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│  2. Code Skill                      │
│  ├─ Crear modelos                   │
│  ├─ Implementar servicios           │
│  ├─ Configurar providers            │
│  └─ CRUD operations                 │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│  3. Workflow Skill                  │
│  ├─ Definir flujos                  │
│  ├─ Conectar componentes            │
│  ├─ Testing                         │
│  └─ Validar UX                      │
└──────────────┬──────────────────────┘
               ↓
┌─────────────────────────────────────┐
│  4. Planner Skill                   │
│  ├─ Automatizar testing             │
│  ├─ Build & Deployment              │
│  ├─ Monitoring                      │
│  └─ Mejoras continuas               │
└─────────────────────────────────────┘
```

---

## 🔄 Ciclo CRUD Completo

### Create
- Design: Form layout
- Code: Model + Service
- Workflow: Navigation + Validation
- Planner: Testing

### Read
- Design: List/Detail screens
- Code: Firestore queries
- Workflow: Real-time sync
- Planner: Performance optimization

### Update
- Design: Edit form
- Code: Update logic
- Workflow: State management
- Planner: Conflict resolution

### Delete
- Design: Confirmation dialog
- Code: Delete operation
- Workflow: Cleanup
- Planner: Soft delete option

---

## 📈 Ejemplos de Uso

### Agregar Nueva Feature

1. **Design:** Crear pantalla en `design-skill.md`
2. **Code:** Implementar en `code-skill.md`
3. **Workflow:** Definir flujo en `workflow-skill.md`
4. **Planner:** Agregar tests en `planner-skill.md`

### Resolver Bug

1. **Workflow:** Entender el flujo afectado
2. **Code:** Identificar servicios/providers
3. **Design:** Verificar UI
4. **Planner:** Agregar test

### Optimizar Performance

1. **Planner:** Perfilar con DevTools
2. **Code:** Optimizar queries/providers
3. **Workflow:** Revisar flujos
4. **Design:** Mejorar UX feedback

---

## 🧪 Testing

### Antes de Deploy

```bash
# 1. Verificar análisis
flutter analyze

# 2. Ejecutar tests
flutter test

# 3. Build APK
flutter build apk --release

# 4. Instalar en dispositivo
flutter install
```

---

## 📚 Documentación

Cada skill incluye:
- ✅ Propósito y responsabilidades
- ✅ Archivos a crear/modificar
- ✅ Ejemplos de código
- ✅ Flujos detallados
- ✅ Checklist de implementación
- ✅ Links a recursos

---

## 🔗 Estructura del Proyecto

```
proyectotallermecanico/
├── .agents/                     ← AGENTE GLOBAL
│   ├── SKILL.md
│   ├── skills/
│   ├── scripts/
│   └── resources/
│
├── lib/
│   ├── main.dart                ← Punto de entrada
│   ├── models/                  ← Modelos de datos
│   ├── services/                ← Servicios Firebase
│   ├── providers/               ← State Management
│   ├── screens/                 ← Pantallas UI
│   ├── widgets/                 ← Componentes
│   └── utils/                   ← Utilidades
│
├── assets/                      ← Imágenes, iconos
├── android/                     ← Config Android
├── ios/                         ← Config iOS
├── test/                        ← Tests unitarios
├── pubspec.yaml                 ← Dependencias
└── README.md
```

---

## 🎯 Checklist Inicial

- [ ] Verificar dependencias: `bash .agents/scripts/verify-dependencies.sh`
- [ ] Configurar Firebase: `bash .agents/scripts/setup-firebase.sh`
- [ ] Inicializar proyecto: `bash .agents/scripts/init-project.sh`
- [ ] Ejecutar app: `flutter run`
- [ ] Leer `design-skill.md`
- [ ] Leer `code-skill.md`
- [ ] Leer `workflow-skill.md`
- [ ] Leer `planner-skill.md`

---

## 🆘 Soporte

### Documentación
- `design-skill.md` - Diseño y UI
- `code-skill.md` - Implementación
- `workflow-skill.md` - Flujos
- `planner-skill.md` - Automatización
- `resources/firebase-setup.md` - Firebase

### Comandos Útiles
```bash
# Verificar todo
bash .agents/scripts/verify-dependencies.sh

# Setup Firebase
bash .agents/scripts/setup-firebase.sh

# Ejecutar app
flutter run

# Análisis estático
flutter analyze

# Tests
flutter test

# Build
flutter build apk --release
```

---

## 🚀 Próximas Fases

### Fase 1: Setup ✅
- [x] Crear agente `.agents`
- [x] Documentar skills
- [x] Scripts de automatización
- [x] Guía Firebase

### Fase 2: Código Base (→ Ahora)
- [ ] Generar archivos Dart
- [ ] Modelos y servicios
- [ ] Providers
- [ ] Pantallas CRUD

### Fase 3: Funcionalidad
- [ ] CRUD completo
- [ ] Navegación
- [ ] Validaciones
- [ ] Manejo de errores

### Fase 4: Polish
- [ ] Animaciones
- [ ] Temas (dark/light)
- [ ] Localization
- [ ] Performance

### Fase 5: Deploy
- [ ] Testing completo
- [ ] Build optimizado
- [ ] Play Store setup
- [ ] Release

---

## 📞 Contacto y Contribuciones

**Autor:** Eliseo128
**Repositorio:** https://github.com/Eliseo128/proyectotallermecanico
**Licencia:** MIT

---

## 📝 Changelog

### v1.0.0 (2026-04-25)
- ✅ Creación del agente `.agents`
- ✅ 4 Skills: Design, Code, Workflow, Planner
- ✅ Scripts de automatización
- ✅ Documentación completa
- ✅ Estructura base del proyecto

---

**¡Bienvenido al proyecto TallerMecanico! 🚗**

El agente `.agents` está listo para guiarte en el desarrollo de tu aplicación móvil. Consulta los skills según tus necesidades.

**Próximo paso:** Lee el skill relevante para tu tarea actual.

---

**Última actualización:** 2026-04-25
