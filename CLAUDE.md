# llamadas_app

App Android (Flutter) para prospección en frío como freelancer de software.

## Quién soy

Leonardo Muñoz (leo). Estoy empezando como freelancer de software y hago llamadas
a negocios locales que encuentro en Google Maps. Esta app es para organizar y
mejorar ese proceso. Estoy aprendiendo: explícame y guíame antes de darme código hecho.

## Cómo hablarme

Español, directo, sin relleno ni resúmenes forzados al final.

## Qué hace la app (objetivo)

1. Mostrar en un mapa los negocios (Google Maps / Places API).
2. Llamar desde la app o detectar los números marcados (historial de llamadas) y tacharlos.
3. Grabar la llamada para saber qué se dijo y acordó.
4. Transcribir y resumir la llamada.
5. Dar retroalimentación de cómo mejorar la forma de vender.

## Plan por fases (MVP)

1. Mapa + lista de negocios + botón de llamar + estado (pendiente / llamado / descartado).
2. Cruce automático con el historial de llamadas (`READ_CALL_LOG`).
3. Importar grabaciones desde la carpeta de la grabadora nativa del teléfono.
4. Transcripción + resumen (Whisper/Deepgram/Gemini + LLM).
5. Coaching de ventas y tendencias entre llamadas.

**Fase actual:** entorno listo (Flutter corre en el celular). Siguiente: API key de
Google y validar cuántos negocios traen teléfono en Places API.

## Decisiones técnicas

- Flutter, probando siempre en el celular real (historial de llamadas y grabaciones no existen en emulador).
- Android no permite a apps de terceros capturar el audio de la línea (Android 9+). Plan:
  usar la grabadora nativa del teléfono y que la app detecte el archivo nuevo.
  Alternativas descartadas por ahora: micrófono con altavoz (mala calidad), VoIP (costo).
- Uso personal por APK, sin publicar en Play Store (por eso `READ_CALL_LOG` es viable).
- Legal: avisar que la llamada puede ser grabada.

## Entorno

- Windows 11, Flutter 3.47.5 en `C:\src\flutter`, Android Studio, SDK en `%LOCALAPPDATA%\Android\Sdk`.
- Dispositivo de pruebas: Xiaomi/Redmi `2207117BPG`, Android 13 (API 33).
- Correr: `flutter run -d PNXS454TW8PR8965`.
- En Xiaomi hay que tener activos "Instalar vía USB" y "Depuración USB (ajustes de seguridad)".

## Reglas

- Nunca subir secrets al repo (API keys de Google, tokens). Van en `.env` o en
  `android/local.properties`, ambos ignorados por git.
- Cada fase se termina y se prueba en el celular antes de pasar a la siguiente.
- Este archivo se mantiene delgado; actualízalo al cerrar cada fase.
