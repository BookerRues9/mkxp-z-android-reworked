ESPAÑOL
# mkxp-z para Android

Este es un puerto de [mkxp-z](https://github.com/mkxp-z/mkxp-z) para Android.

Actualmente, funciona *casi* correctamente (probablemente, *experimentalmente*),
pero lo suficiente como para ejecutar los juegos RPG Maker XP
repositorio original de [mkxp-z-android] (https://github.com/thehatkid/mkxp-z-android)

## Ejecutar mkxp-z en Android

0. ~~Crear la aplicación mkxp-z~~
1. Instalar el APK en tu dispositivo Android
2. Crear la carpeta `mkxp-z` en el almacenamiento interno (p. ej. `/storage/emulated/0/mkxp-z`)
3. Puedes poner una configuración personalizada de mkxp-z ([mkxp.json](app/jni/mkxp-z/mkxp.json)) en la carpeta `mkxp-z`
(p. ej., precargar scripts o cambiar el directorio del juego para cargar el juego desde el almacenamiento externo)
4. Copiar los archivos del juego en la carpeta `mkxp-z`
(o en otra carpeta del juego definida en tu `mkxp.json`)
5. Ejecutar mkxp-z, conceder acceso al almacenamiento y divertirse, ¿creo?

## Problemas conocidos

- No puedes escribir partidas guardadas/archivos en almacenamiento externo (como la tarjeta SD) en versiones anteriores a Android 10
(En Android 11+, otorgar acceso a todos los archivos significa que puedes escribir en almacenamientos externos)

## Por hacer...
- Corregir la compilación de extensiones Ruby en el entorno MSYS2 de Windows
- *...y mucho más, ¿creo?*

## Tutotial
## requisitos 
- Ubuntu ubuntu-22.04
- Android Studio ultima version
- android SDK y NDK 23.2.8568313
- Ruby version 3.0+
- cmake build tools
## preparación del entorno
- primero actualizamos dependencias : sudo apt update
- en la consola de ubuntu instalamos : sudo apt install build-essential cmake ruby-full
- instalamos rvm : 
- sudo apt install curl gpg -y
- curl -sSL https://get.rvm.io/ | bash
- source ~/.rvm/scripts/rvm
- después ejecutamos este comando al finalizar usamos ruby -v
- rvm install 3.1
- rvm use 3.1 --default
## clonamos el repositorio 
- git clone https://github.com/BookerRues9/mkxp-z-android-reworked.git
## abrimos en la consola el proyecto de mkxp-z-android
- luego vamos a : cd app/jni
- descargamos las dependencias : chmod +x get_deps.sh
- ejecutamos el archivo : chmod +x get_deps.sh
## luego de descargar las dependencias damos las rutas donde se ubica todo ejecutamos los siguientes comandos 
- export ANDROID_HOME=/home/TUUSUARIO/Android/Sdk
- export ANDROID_NDK_HOME=$ANDROID_HOME/ndk/23.2.8568313
- export ARCH=linux-x86_64
- export PATH=$ANDROID_NDK_HOME/toolchains/llvm/prebuilt/$ARCH/bin:$PATH
## compilar las dependencias
## **para 32 bits**
- HOST=armv7a-linux-androideabi TARGET=arm-linux-androideabi ABI=armeabi-v7a
## **para 64 bits**
- HOST=aarch64-linux-android TARGET=aarch64-linux-android ABI=arm64-v8a make
- si quieres compilar solamente pon make
## luego de compilar las dependencias abre el proyecto en android studio y compila el apk 
