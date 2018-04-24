---
title: Visual C++ para desarrollo móvil multiplataforma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 00f5bcdbdd84de3a33914d3ea90f4eb00c960f1f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ para el desarrollo móvil multiplataforma.
Puede compilar aplicaciones nativas de C++ para dispositivos iOS, Android y Windows, y compartir código común en bibliotecas compiladas para iOS, Android y Windows mediante Visual C++ para desarrollo móvil multiplataforma. Se trata de una opción disponible en Visual Studio de 2015 que instala los SDK y las herramientas que necesita para el desarrollo multiplataforma de bibliotecas compartidas y las aplicaciones nativas. Cuando se instala, puede usar Visual C++ para crear código que se ejecuta dispositivos y plataformas iOS y Android, además de en Windows, Windows Phone y Xbox.  
  
 Escribir código para varias plataformas puede resultar frustrante. Los principales lenguajes de desarrollo y herramientas para iOS, Android y Windows son distintos en cada plataforma. Sin embargo, todas las plataformas admiten la escritura de código en C++. Este es el denominador común que puede usar para volver a usar el código principal en las distintas plataformas. El código nativo escrito en C++ ofrece un rendimiento superior y mayor resistencia frente a la ingeniería inversa. La reutilización de código puede ahorrarle tiempo y esfuerzos en la creación de aplicaciones para varias plataformas.  
  
 El desarrollo con Visual C++ para el desarrollo móvil multiplataforma ofrece varias ventajas:  
  
1.  **Instalación sencilla.** El instalador de Visual Studio adquiere e instala las herramientas necesarias de terceros y los SDK que necesita para crear aplicaciones o bibliotecas para iOS y Android. La Instalación y configuración es sencilla y casi automática.  
  
2.  **Un entorno de compilación eficaz y familiar.** Cree proyectos y soluciones multiplataforma que se pueden compartir fácilmente con plantillas de Visual Studio. Administre las propiedades de todos los proyectos con una interfaz común. Edite el código en el editor de Visual Studio y saque partido de las características de IntelliSense multiplataforma integradas de terminación de código y resaltado de errores.  
  
3.  **Experiencia de depuración unificada.** Use las herramientas de depuración de talla mundial de Visual Studio para ver y analizar el código de C++ en todas las plataformas, incluidos los dispositivos Android y emuladores, simuladores de iOS y dispositivos y dispositivos de Windows o Windows Phone y emuladores.  
  
## <a name="get-the-tools"></a>Obtener las herramientas  
 Visual C++ para el desarrollo móvil multiplataforma es un componente opcional instalable incluido en Visual Studio 2015. Para obtener información sobre los requisitos previos y las instrucciones de instalación, vea [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Para compilar código para iOS, también necesitará un equipo Mac y un cuenta de desarrollador de Apple iOS. Para obtener más información, consulta [Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Alcance rápidamente el nivel requerido  
 Si tiene experiencia con el desarrollo Android o iOS, tenemos material excelente para que pueda empezar a trabajar. Visual Studio es un entorno de desarrollo expresivo y con capacidad. Para obtener información sobre cómo usarlo, pruebe con las guías [Introducción para desarrolladores de Android](/previous-versions/windows/apps/dn275875\(v=win.10\)) o [Introducción para desarrolladores de iOS](/previous-versions/windows/apps/jj657966\(v=win.10\)). Estos temas presentan Visual Studio y los conceptos que necesitará para desarrollar aplicaciones multiplataforma para Windows y Windows Phone. Para empezar a programar su primera aplicación multiplataforma para iOS y Android, vea [Build an OpenGL ES Application on Android and iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ para el desarrollo móvil multiplataforma incluye varias plantillas para ayudarle a iniciarse en sus aplicaciones:  
  
-   Aplicación OpenGLES 2 (Android, iOS, Windows Universal)  
  
     Crea una solución que incluye un conjunto de proyectos para compilar una aplicación de actividad nativa de Android, una aplicación de iOS y una aplicación universal de Windows, junto con una biblioteca de código compartido de C++. Estas aplicaciones usan bibliotecas específicas de plataforma creadas con código C++ OpenGL ES común para diseñar el mismo cubo giratorio en cada aplicación. Para poder usar esta plantilla, debe incluir la opción Herramientas de desarrollo de aplicaciones universales de Windows al instalar Visual Studio.  
  
-   Aplicación de actividad nativa (Android)  
  
     Crea una aplicación OpenGL de C++ completa como proyecto de actividad nativa Android.  
  
-   Aplicación OpenGL ES (Android e iOS)  
  
     Crea una solución con un conjunto de proyectos para compilar una aplicación Android Native Activity y una aplicación de iOS. Estas aplicaciones usan bibliotecas específicas de plataforma creadas con código C++ OpenGL ES común para diseñar el mismo cubo giratorio en cada aplicación.  
  
-   Biblioteca compartida (Android, iOS)  
  
     Crea una solución con proyectos para crear un archivo de biblioteca dinámica Android (.so) y un archivo de biblioteca estática (.a) de iOS mediante código común de C++ en un proyecto compartido.  
  
-   Aplicación básica (Android, Ant)  
  
     Crea un proyecto de aplicación "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Ant.  
  
-   Aplicación básica (Android, Gradle)  
  
     Crea un proyecto de aplicación "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Gradle.  
  
-   Biblioteca básica (Android, Ant)  
  
     Crea un proyecto de biblioteca "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Ant.  
  
-   Biblioteca básica (Android, Gradle)  
  
     Crea un proyecto de biblioteca "Hola mundo" de Android que usa solo código fuente Java y el sistema de compilación Gradle.  
  
-   Biblioteca dinámica compartida (Android)  
  
     Crea un archivo de biblioteca dinámica Android (.so) mediante código C++.  
  
-   Aplicación OpenGLES 2 (iOS)  
  
     Crea una solución con un conjunto de proyectos para compilar una aplicación OpenGL ES 2 de iOS. La aplicación usa una biblioteca de código de C++ OpenGL ES para dibujar el cubo girando en una aplicación iOS. Esta aplicación puede ser un buen punto de partida para ver cómo importar bibliotecas de C++ en su aplicación iOS.  
  
-   Biblioteca estática (Android)  
  
     Crea un proyecto para compilar una biblioteca estática para Android. Solo puede vincular una biblioteca dinámica en una aplicación Android; sin embargo, podrá vincular tantas bibliotecas estáticas como desee.  
  
-   Biblioteca estática (iOS)  
  
     Crea un proyecto para compilar una biblioteca estática para iOS.  
  
-   Proyecto de archivos Make (Android)  
  
     Crea un contenedor de proyecto para sus propios proyectos de archivos Make de Android.  
  
## <a name="try-out-sample-code"></a>Pruebe el código de muestra  
 Descargue los ejemplos que muestran cómo crear bibliotecas de código compartido que puede usar en aplicaciones de iOS, Android y Windows y cómo crear aplicaciones de actividad nativa completas para Android. Para comenzar, vea [Cross-Platform Mobile Development Examples](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>En esta sección  
  
1.  [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Crear una aplicación de actividad nativa de Android](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Build an OpenGL ES Application on Android and iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Cross-Platform Mobile Development Examples](../cross-platform/cross-platform-mobile-development-examples.md)