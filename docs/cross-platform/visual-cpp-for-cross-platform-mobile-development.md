---
title: Desarrollo móvil multiplataforma con C++ | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 61bb3e17b104759995852959a7396d5a76927cfb
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589038"
---
# <a name="cross-platform-mobile-development-with-c"></a>Desarrollo móvil multiplataforma con C++

Puede compilar aplicaciones de C++ nativas para dispositivos iOS, Android y Windows usando las herramientas multiplataforma disponibles en Visual Studio. **Desarrollo móvil con C++** es una carga de trabajo disponible en el Instalador de Visual Studio. Instala los SDK y las herramientas que necesita para el desarrollo multiplataforma de bibliotecas compartidas y las aplicaciones nativas. Cuando se instala, puede usar C++ para crear código que se ejecuta en dispositivos y plataformas iOS y Android, además de en Windows, Windows Store y Xbox.

Escribir código para varias plataformas a menudo resulta frustrante. Los principales lenguajes de desarrollo y herramientas para iOS, Android y Windows son distintos en cada plataforma. Sin embargo, todas las plataformas admiten la escritura de código en C++. Este es el denominador común que puede habilitar la reutilización de código principal en las distintas plataformas. El código nativo escrito en C++ ofrece un rendimiento superior y mayor resistencia frente a la ingeniería inversa. La reutilización de código puede ahorrarle tiempo y esfuerzos en la creación de aplicaciones para varias plataformas.

El desarrollo con C++ para el desarrollo móvil multiplataforma ofrece varias ventajas:

- **Instalación sencilla.** El instalador de Visual Studio adquiere e instala las herramientas necesarias de terceros y los SDK que necesita para crear aplicaciones o bibliotecas para iOS y Android. La instalación y configuración son sencillas y casi automática.

- **Un entorno de compilación eficaz y familiar.** Cree proyectos y soluciones multiplataforma que se pueden compartir fácilmente con plantillas de Visual Studio. Administre las propiedades de todos los proyectos con una interfaz común. Edite el código en el editor de Visual Studio y saque partido de las características de IntelliSense multiplataforma integradas de terminación de código y resaltado de errores.

- **Experiencia de depuración unificada.** Use las herramientas de depuración de primer nivel de Visual Studio para ver y recorrer paso a paso el código de C++ en todas las plataformas: Dispositivos y emuladores de Android, simuladores y dispositivos de iOS y emuladores y dispositivos de Windows Store o Windows.

## <a name="get-the-tools"></a>Obtener las herramientas

Desarrollo móvil con C++ móviles es una carga de trabajo instalable que se proporciona con Visual Studio. Para información sobre los requisitos previos y las instrucciones de instalación, vea [Instalación del desarrollo móvil multiplataforma con C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Para compilar código para iOS, también necesitará un equipo Mac y un cuenta de desarrollador de Apple iOS. Para obtener más información, vea [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md) (Instalar y configurar herramientas para compilar con iOS).

## <a name="come-up-to-speed"></a>Alcance rápidamente el nivel requerido

Si tiene experiencia con el desarrollo Android o iOS, tenemos material excelente para que pueda empezar a trabajar. Visual Studio es un entorno de desarrollo expresivo y con capacidad. Para obtener información sobre cómo usarlo, pruebe con las guías [Introducción para desarrolladores de Android](/previous-versions/windows/apps/dn275875\(v=win.10\)) o [Introducción para desarrolladores de iOS](/previous-versions/windows/apps/jj657966\(v=win.10\)). Estos artículos presentan Visual Studio y los conceptos que necesitará para desarrollar aplicaciones multiplataforma para Windows y Windows Store. Para empezar a programar su primera aplicación multiplataforma para iOS y Android, vea [Crear una aplicación de OpenGL ES en Android e iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).

La carga de trabajo Desarrollo móvil con C++ incluye varias plantillas para ayudarle a iniciarse en sus aplicaciones:

- Aplicación OpenGLES 2 (Android, iOS, Windows Universal)

  Crea una solución que incluye un conjunto de proyectos para compilar una aplicación de actividad nativa de Android, una aplicación de iOS y una aplicación universal de Windows, junto con una biblioteca de código compartido de C++. Estas aplicaciones usan bibliotecas específicas de plataforma creadas con código C++ OpenGL ES común para diseñar el mismo cubo giratorio en cada aplicación. Para usar esta plantilla, incluya la carga de trabajo **Desarrollo de la plataforma universal de Windows** cuando instale Visual Studio.

- Aplicación de actividad nativa (Android)

  Crea una aplicación OpenGL de C++ completa como proyecto de actividad nativa Android.

- Aplicación OpenGL ES (Android e iOS)

  Crea una solución con un conjunto de proyectos para compilar una aplicación Android Native Activity y una aplicación de iOS. Estas aplicaciones usan bibliotecas específicas de plataforma creadas con código C++ OpenGL ES común para diseñar el mismo cubo giratorio en cada aplicación.

- Biblioteca compartida (Android, iOS)

  Crea una solución con proyectos para crear un archivo de biblioteca dinámica Android (.so) y un archivo de biblioteca estática (.a) de iOS mediante código común de C++ en un proyecto compartido.

- Aplicación básica (Android, Ant)

  Crea un proyecto de aplicación "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Ant.

- Aplicación básica (Android, Gradle)

  Crea un proyecto de aplicación "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Gradle.

- Biblioteca básica (Android, Ant)

  Crea un proyecto de biblioteca "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Ant.

- Biblioteca básica (Android, Gradle)

  Crea un proyecto de biblioteca "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Gradle.

- Biblioteca dinámica compartida (Android)

  Crea un archivo de biblioteca dinámica Android (.so) mediante código C++.

- Aplicación OpenGLES 2 (iOS)

  Crea una solución con un conjunto de proyectos para compilar una aplicación OpenGL ES 2 de iOS. La aplicación usa una biblioteca de código de C++ OpenGL ES para dibujar el cubo girando en una aplicación iOS. Esta aplicación puede ser un buen punto de partida para ver cómo importar bibliotecas de C++ en su aplicación iOS.

- Biblioteca estática (Android)

  Crea un proyecto para compilar una biblioteca estática para Android. Solo puede vincular una biblioteca dinámica en una aplicación Android; sin embargo, podrá vincular tantas bibliotecas estáticas como desee.

- Biblioteca estática (iOS)

  Crea un proyecto para compilar una biblioteca estática para iOS.

- Proyecto de archivos Make (Android)

  Crea un contenedor de proyecto para sus propios proyectos de archivos Make de Android.

## <a name="try-out-sample-code"></a>Pruebe el código de muestra

Descargue los ejemplos que muestran cómo crear bibliotecas de código compartido que puede usar en aplicaciones de iOS, Android y Windows. Y vea ejemplos de cómo crear aplicaciones native-activity para Android. Para comenzar, vea [Ejemplos de desarrollo móvil multiplataforma](../cross-platform/cross-platform-mobile-development-examples.md).

## <a name="see-also"></a>Vea también

[Instalación del desarrollo móvil multiplataforma con C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)\
[Instalación y configuración de herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)\
[Creación de una aplicación native-activity para Android](../cross-platform/create-an-android-native-activity-app.md)\
[Creación de una aplicación de OpenGL ES en Android e iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)\
[Ejemplos de desarrollo móvil multiplataforma](../cross-platform/cross-platform-mobile-development-examples.md)
