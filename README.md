# ROSE AI — Native Android Project (Kotlin + Jetpack Compose)

This is a native Android Studio / Gradle project, not a Flutter project.

## Folder structure

```text
ROSE_AI/
├── .github/workflows/build-apk.yml
├── app/
│   ├── build.gradle
│   └── src/main/
│       ├── AndroidManifest.xml
│       └── java/com/rose/ai/
│           ├── MainActivity.kt
│           ├── AIManager.kt
│           ├── ApiSettings.kt
│           ├── ApiSettingsScreen.kt
│           └── ChatScreen.kt
├── gradle/wrapper/gradle-wrapper.properties
├── build.gradle
├── settings.gradle
├── gradle.properties
└── README.md
```

## Build APK on GitHub
1. Create a new GitHub repository.
2. Extract this ZIP and upload all files/folders inside `ROSE_AI_NATIVE` to the repository root.
3. Open **Actions** → **Build ROSE AI APK** → **Run workflow**, or push to `main`.
4. Download the `ROSE-AI-release` artifact from the completed workflow.

The workflow installs Gradle 8.9 and builds `:app:assembleRelease`. The output is an unsigned release APK. Android may show an install warning for an unsigned APK; production distribution needs a signing key.

## Build in Android Studio
Open the project root (`settings.gradle` location) in Android Studio. Use Gradle 8.9 and JDK 17. If Android Studio asks for a Gradle wrapper, use the configured distribution URL in `gradle/wrapper/gradle-wrapper.properties` or select a local Gradle 8.9 installation.

## AI providers
Open the app → menu/settings → AI API Manager. Select a provider, paste its API key, edit the model ID if needed, save and test.

| Provider | API Base URL | Default model |
|---|---|---|
| Groq | https://api.groq.com/openai/v1 | llama-3.3-70b-versatile |
| OpenRouter | https://openrouter.ai/api/v1 | openai/gpt-4o-mini |
| Mistral | https://api.mistral.ai/v1 | mistral-small-latest |
| Google Gemini | https://generativelanguage.googleapis.com/v1beta | gemini-2.0-flash |

Gemini uses native `generateContent`; Groq, OpenRouter and Mistral use OpenAI-compatible `/chat/completions`.

## Security and limitations
- API keys are stored on-device with AndroidX EncryptedSharedPreferences. Never put real keys in source code or GitHub.
- A key in a mobile client can ultimately be extracted by a determined attacker. A public app should call a private backend proxy with authentication and rate limits.
- This starter includes the neon dashboard, provider settings, connection test and text chat. The central girl is a decorative placeholder, not a full 3D animated model. Voice recognition, camera/QR scan, weather, persistent memories, and automated actions in third-party apps are not implemented in this version.
- Provider availability and model IDs can change. No project can promise 100% uptime.
