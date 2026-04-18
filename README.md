# TCC Hub

Repositório acadêmico colaborativo voltado para compartilhamento e descoberta de Trabalhos de Conclusão de Curso (TCCs) e artigos científicos.

Atualmente este repositório contém a base Android (template GoNative/Median) usada para empacotar e distribuir a experiência mobile.

## Visão geral técnica

- Plataforma: Android (Gradle + Kotlin/Java)
- Módulo principal: `:app`
- Build tools: AGP 8.13.2
- JDK recomendado: 21

## Pré-requisitos

- JDK 21 instalado
- Gradle Wrapper disponível no repositório
- Android SDK com `compileSdk` 36

## Estrutura relevante

- `app/build.gradle`: configuração do app Android, flavors e dependências
- `plugins.gradle`: descoberta e integração de plugins locais/compilados
- `dependencies.json`: versões de core/engine e plugins compilados
- `.github/workflows/android-ci-build.yml`: pipeline de build em CI

## Configuração local

### 1) Arquivo de configuração do app

O build lê `app/src/main/assets/appConfig.json` para preencher integrações opcionais (OneSignal, Facebook, AdMob, Auth0, Branch etc.).

### 2) Firebase (opcional)

Se o plugin `google-services` estiver habilitado, inclua `app/google-services.json` com `applicationId` compatível com o app.

### 3) Assinatura (release/upload)

As credenciais de assinatura são lidas via propriedades Gradle ou variáveis de ambiente:

- `RELEASE_STORE_FILE`, `RELEASE_STORE_PASSWORD`, `RELEASE_KEY_ALIAS`, `RELEASE_KEY_PASSWORD`
- `UPLOAD_STORE_FILE`, `UPLOAD_STORE_PASSWORD`, `UPLOAD_KEY_ALIAS`, `UPLOAD_KEY_PASSWORD`

Exemplo em `~/.gradle/gradle.properties` (não versionar):

```properties
RELEASE_STORE_FILE=/caminho/release.keystore
RELEASE_STORE_PASSWORD=********
RELEASE_KEY_ALIAS=release
RELEASE_KEY_PASSWORD=********

UPLOAD_STORE_FILE=/caminho/upload.keystore
UPLOAD_STORE_PASSWORD=********
UPLOAD_KEY_ALIAS=upload
UPLOAD_KEY_PASSWORD=********
```

## Comandos úteis

```bash
./gradlew tasks
./gradlew assembleDebug
./gradlew :app:assembleDebug
```

## CI

A pipeline de CI executa build de debug e publica o APK como artifact.

## Autor

Adilson C. Rafael

GitHub: https://github.com/adilson889
