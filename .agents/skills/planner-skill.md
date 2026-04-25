# ⏱️ Skill Planificador - TallerMecanico

## Propósito
Automatizar tareas de setup, testing, building y deployment del proyecto.

---

## 🚀 Scripts de Automatización

### 1. verify-dependencies.sh
**Objetivo:** Verificar que todas las herramientas necesarias estén instaladas.

```bash
#!/bin/bash
set -e

echo "🔍 Verificando dependencias..."
echo ""

# Flutter
echo -n "Flutter: "
flutter --version | head -1

# Dart
echo -n "Dart: "
dart --version | head -1

# Firebase CLI
echo -n "Firebase: "
firebase --version

echo ""
echo "📊 Flutter Doctor:"
flutter doctor -v

echo ""
echo "✅ Todas las herramientas están OK"
```

**Uso:**
```bash
bash .agents/scripts/verify-dependencies.sh
```

**Verifica:**
- ✅ Flutter instalado (v3.0+)
- ✅ Dart instalado (v2.17+)
- ✅ Firebase CLI instalado
- ✅ Android SDK disponible
- ✅ Emuladores/dispositivos conectados

---

### 2. setup-firebase.sh
**Objetivo:** Configurar Firebase en el proyecto.

```bash
#!/bin/bash

echo "🔥 Configurando Firebase..."
echo ""

read -p "¿Ya tienes proyecto en Firebase Console? (s/n): " response

if [[ $response == "s" ]]; then
  read -p "Ingresa PROJECT_ID: " PROJECT_ID
  firebase use $PROJECT_ID
  echo "✅ Proyecto configurado: $PROJECT_ID"
else
  echo "1. Visita: https://console.firebase.google.com"
  echo "2. Crear proyecto 'TallerMecanico'"
  echo "3. Agregar app Android (paquete: com.example.proyectotallermecanico)"
  echo "4. Descargar google-services.json"
  echo "5. Copiar a: android/app/google-services.json"
  echo ""
  read -p "Presiona Enter cuando termines..."
fi

echo ""
echo "✅ Setup Firebase completado"
```

**Uso:**
```bash
bash .agents/scripts/setup-firebase.sh
```

**Realiza:**
- ✅ Login en Firebase CLI
- ✅ Seleccionar proyecto
- ✅ Guiar descarga de google-services.json
- ✅ Verificar Firestore Database
- ✅ Configurar colecciones

---

### 3. init-project.sh
**Objetivo:** Inicializar estructura del proyecto.

```bash
#!/bin/bash

echo "🚀 Inicializando proyecto TallerMecanico..."
echo ""

# Obtener dependencias
echo "📦 flutter pub get..."
flutter pub get

echo ""
echo "✅ Proyecto inicializado"
echo "📝 Siguiente: flutter run"
```

**Uso:**
```bash
bash .agents/scripts/init-project.sh
```

**Realiza:**
- ✅ Descargar dependencias (pubspec.yaml)
- ✅ Generar archivos generados
- ✅ Compilar assets

---

## 📋 Tareas Automatizadas

### Build & Compilation

```bash
# Debug mode
flutter run

# Release mode
flutter run --release

# Build APK
flutter build apk --release

# Build AAB (Play Store)
flutter build appbundle --release

# Build Web
flutter build web --release

# Limpiar caché
flutter clean && flutter pub get
```

---

### Testing (Próximo)

```bash
# Run all tests
flutter test

# Coverage
flutter test --coverage

# Integration tests
flutter drive --target=test_driver/app.dart
```

---

### Code Quality (Próximo)

```bash
# Analyzer
flutter analyze

# Format
dart format lib/

# Lint
flutter pub run flutter_lints
```

---

## 🔄 CI/CD Pipeline (Próximo)

### GitHub Actions Workflow

```yaml
name: Build & Test

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Setup Flutter
      uses: subosito/flutter-action@v2
      with:
        flutter-version: '3.0.0'
    
    - name: Get dependencies
      run: flutter pub get
    
    - name: Analyze
      run: flutter analyze
    
    - name: Run tests
      run: flutter test
    
    - name: Build APK
      run: flutter build apk --release
    
    - name: Upload APK
      uses: actions/upload-artifact@v3
      with:
        name: app-release.apk
        path: build/app/outputs/flutter-apk/app-release.apk
```

---

## 📊 Deployment

### Play Store
```bash
# 1. Generar keystore
keytool -genkey -v -keystore ~/upload-keystore.jks \
  -keyalg RSA -keysize 2048 -validity 10000 \
  -alias upload

# 2. Configurar build.gradle
# 3. Build AAB
flutter build appbundle --release

# 4. Upload a Play Console
# https://play.google.com/console
```

### Firebase Hosting (Web)
```bash
# 1. Build web
flutter build web --release

# 2. Deploy
firebase deploy --only hosting
```

---

## 🧪 Estrategia de Testing

### Pruebas Unitarias
```dart
test('AutomovilModel.toJson', () {
  final automovil = AutomovilModel(...);
  final json = automovil.toJson();
  expect(json['marca'], 'Toyota');
});
```

### Pruebas de Widget
```dart
testWidgets('AutomovilListScreen displays list', (WidgetTester tester) async {
  await tester.pumpWidget(const MyApp());
  expect(find.byType(ListView), findsOneWidget);
});
```

### Pruebas de Integración
```dart
// test_driver/app.dart
void main() => enableFlutterDriverExtension();

// test_driver/app_test.dart
void main() {
  group('TallerMecanico App', () {
    final SerializableFinder automovilesList = find.byType('ListView');
    
    testWidgets('displays automoviles list', (WidgetTester tester) async {
      await tester.pumpWidget(const MyApp());
      expect(automovilesList, findsOneWidget);
    });
  });
}
```

---

## 📈 Monitoreo y Logging

### Firebase Crashlytics (Próximo)
```dart
import 'package:firebase_crashlytics/firebase_crashlytics.dart';

// Capturar excepciones
FirebaseCrashlytics.instance.recordError(error, stackTrace);
```

### Logging Custom
```dart
import 'package:logger/logger.dart';

final logger = Logger();
logger.i('Info message');
logger.d('Debug message');
logger.w('Warning message');
logger.e('Error message');
```

---

## 📅 Checklist de Deployment

- [ ] Pruebas unitarias pasadas
- [ ] Pruebas de widgets pasadas
- [ ] Análisis estático OK
- [ ] Linting OK
- [ ] No hay warnings críticos
- [ ] Version bumped en pubspec.yaml
- [ ] Changelog actualizado
- [ ] README.md actualizado
- [ ] Build APK exitoso
- [ ] APK probada en dispositivo/emulador
- [ ] Play Store metadata preparado
- [ ] Privacy policy actualizada
- [ ] Screenshots y descripción listos
- [ ] Release notes escritas

---

## 🔐 Seguridad

### Secretos y Credentials
```bash
# Variables de entorno
export FIREBASE_PROJECT_ID="tu-proyecto"
export FIREBASE_API_KEY="tu-api-key"

# .env (no subir a Git)
FIREBASE_PROJECT_ID=xxx
FIREBASE_API_KEY=xxx
```

### Git Secrets
```bash
# .gitignore debe incluir:
.env
google-services.json
firebase-debug.log
build/
.dart_tool/
```

---

## 🚨 Troubleshooting

### Problemas Comunes

#### Error: "Gradle build failed"
```bash
flutter clean
flutter pub get
flutter build apk --release
```

#### Error: "No connected devices"
```bash
# Listar dispositivos
flutter devices

# Conectar emulador
emulator -list-avds
emulator -avd <nombre>
```

#### Error: "Firebase project not found"
```bash
firebase projects:list
firebase use <project-id>
```

---

## 📚 Recursos

- [Flutter Documentation](https://flutter.dev/docs)
- [Firebase Console](https://console.firebase.google.com)
- [Play Store Console](https://play.google.com/console)
- [GitHub Actions](https://github.com/features/actions)
- [Flutter Testing](https://flutter.dev/docs/testing)

---

## ✅ Checklist del Planificador

- [ ] Scripts de verificación funcionando
- [ ] Firebase setup automatizado
- [ ] Proyecto inicializa correctamente
- [ ] Build APK/AAB OK
- [ ] Tests unitarios creados
- [ ] Tests de widget creados
- [ ] CI/CD pipeline configurado
- [ ] Deployment a Play Store documentado
- [ ] Monitoreo implementado
- [ ] Seguridad validada

---

**Última actualización:** 2026-04-25
