# Panalink — Demo pública del cliente Android

Esta es una **copia pública de demostración** de la interfaz Android de Panalink(Kotlin + Jetpack Compose + Material 3), publicada **exclusivamente como portafolio** para que colaboradores potenciales evalúen la arquitectura y el estilo de código.

> ⚠️ **NO es la aplicación oficial.** Este repo contiene **solo la UI/cliente**, con **todos los servicios de backend reemplazados por placeholders**(no hay Supabase real, no hay vCDN, no hay keystores de producción, no hay servidores). Sin tus propias credenciales y backend, la app **compila pero no funciona de punta a punta**.

## ✨ Qué es(arquitectura que puedes evaluar)

- **Mensajería 1:1 en tiempo real**(estados sending → sent → delivered → read, persistencia Room offline-first, sync con Supabase Realtime).
- **Salas de voz estilo StarMaker**(colgantes de avatar, efectos de entrada, señalización en tiempo real).
- **Reels tipo TikTok**(pool de ExoPlayers con preload adaptativo y refresh de URLs firmadas).
- **Lives con cámara**(LiveKit, glassmorphism, regalos animados sincronizados por Realtime).
- **Stories de 24 h**, feed, perfiles, stickers y emojis.
.
 **Arquitectura:** MVVM con repositorios, Room + WorkManager(offline-first), singleton de signaling, y un estricto control de regresiones documentado en el código.

## 🛠️ Stack

Kotlin · Jetpack Compose · Material 3 · Room · WorkManager · ExoPlayer · LiveKit · Coil · Retrofit · Supabase-kt · Gradle 9.3.1

## 🚀 Compilar(debug)

```bash
# Requisitos: JDK 17+, Android SDK (compileSdk 35.
./gradlew :app:compileDebugKotlin
# o el APK completo:
./gradlew :app:assembleDebug
```

- `app/google-services.json` es **dummy** y está commititeado (placeholders) para que compile sin configuración.
- `app/secrets.defaults.properties` está vacío (requerido por el plugin de secrets).

## 🔌 Configuración real(para hacerla funcionar de verdad)

1. Creá tu proyecto **Supabase** y reemplazá los placeholders en `app/src/main/java/com/example/data/supabase/SupabaseClient.kt`.
2. Reemplazá los hosts `*.example.invalid` de `VcdnUrlResolver.kt`, `VcdnDeleter.kt`, `CdnManager.kt`, etc,por tus endpoints reales de CDN/firma.
.
 Creá tu canal de distribución OTA reemplazando `YOUR_OWNER`/`YOUR_RELEASE_REPO` en `UpdateViewModel.kt`.

## 📄 Licencia

**Solo demo.** Todos los derechos reservados por el mantenedor. Este código se publica para **evaluación y portafolio**— no se conceden derechos de uso, copia ni distribución fuera de lo permitido por escrito. Para colaborar en el proyecto real, abrí un issue indicando tu interés y seguí el [CONTRIBUTING.md](CONTRIBUTING.md) del repositorio privado.