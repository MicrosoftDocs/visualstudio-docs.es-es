---
title: Crear una aplicación de actividad nativa de Android | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6bc8d96c6207889f07ec6bf1257be3d620855fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731423"
---
# <a name="create-an-android-native-activity-app"></a>Crear una aplicación de Android Native Activity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cuando se instala la opción Visual C++ para el desarrollo móvil multiplataforma, Visual Studio 2015 puede usarse para crear aplicaciones de Android Native Activity completamente funcionales. El kit de desarrollo nativo (NDK) de Android es un conjunto de herramientas que le permite implementar la mayor parte de su aplicación para Android mediante código de C/C++ puro. El código Java JNI actúa como adherencia para permitir que el código C/C++ interactúe con Android. El NDK de Android introdujo la capacidad para crear aplicaciones Native Activity con la API de Android Level 9. El código Native Activity se usa para crear aplicaciones de juegos y gráficos avanzados que usan Unreal Engine u OpenGL. Este tema le guiará en el proceso de creación de una aplicación Native Activity sencilla que usa OpenGL. Existen temas adicionales que abordan el ciclo de vida de desarrollador al completo incluida la edición, la compilación, la depuración y la implementación de código Native Activity.  
  
 [Requisitos](#req)   
 [Crear un nuevo proyecto de Native Activity](#Create)   
 [Compilar y ejecutar la aplicación predeterminada Native Activity de Android](#BuildHello)  
  
##  <a name="req"></a> Requisitos  
 Antes de crear una aplicación de Android Native Activity, asegúrese de que cumple todos los requisitos del sistema y de que tiene instalada la opción Visual C++ para el desarrollo móvil multiplataforma en Visual Studio 2015. Para obtener más información, consulta [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Asegúrese de que las herramientas de terceros y SDK necesarios estén incluidos en la instalación y que está instalado el emulador de Microsoft Visual Studio para Android.  
  
##  <a name="Create"></a> Crear un nuevo proyecto de Native Activity  
 En este tutorial, primero debe crear un nuevo proyecto de Android Native Activity y, a continuación, compilar y ejecutar la aplicación predeterminada en el emulador de Visual Studio para Android.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1. Abra Visual Studio. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2. En el cuadro de diálogo **Nuevo proyecto** , debajo de **Plantillas**, elija **Visual C++**, **Multiplataforma**y luego elija la plantilla **Aplicación de Native-Activity (Android)** .  
  
3. Ponga a la aplicación un nombre como `MyAndroidApp`y luego elija **Aceptar**.  
  
    ![Crear un proyecto de actividad nativa](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Visual Studio crea la solución nueva y abre el Explorador de soluciones.  
  
    ![Proyecto de actividad nativa en el Explorador de soluciones](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   La nueva solución de aplicaciones Native Activity de Android incluye dos proyectos:  
  
-   **MyAndroidApp.NativeActivity** contiene las referencias y el código de adherencia para que su aplicación se ejecute como Native Activity en Android. La implementación de los puntos de entrada del código de adherencia está en main.cpp. Los encabezados precompilados están en pch.h. Su proyecto de aplicación de Native Activity se compila en un archivo de biblioteca compartida (.so) que selecciona el proyecto Packaging.  
  
-   **MyAndroidApp.Packaging** crea el archivo .apk para la implementación en un emulador o dispositivo Android. Este contiene los recursos y el archivo AndroidManifest.xml donde se establecen las propiedades del manifiesto. También contiene el archivo build.xml que controla el proceso de compilación de Ant. Se establece como proyecto de inicio de manera predeterminada para que se pueda implementar y ejecutar directamente desde Visual Studio.  
  
##  <a name="BuildHello"></a> Compilar y ejecutar la aplicación predeterminada Native Activity de Android  
 Compile y ejecute la aplicación generada por la plantilla para comprobar su instalación y configuración. Para realizar esta prueba inicial, ejecute la aplicación en uno de los perfiles de dispositivo que instala el emulador de Visual Studio para Android. Si prefiere probar la aplicación en otro destino, cargue el emulador de destino o conecte el dispositivo a su equipo.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Para compilar y ejecutar la aplicación Native Activity predeterminada  
  
1.  Si aún no está seleccionada, elija la opción **x86** en la lista desplegable **Plataformas de solución** .  
  
     ![Selección de x86 en el menú desplegable Plataformas de solución](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Si la lista **Plataformas de solución** no aparece, elija **Plataformas de solución** en la lista desplegable **Agregar o quitar botones** y luego elija la plataforma.  
  
2.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
     La ventana Salida muestra la salida del proceso de compilación para los dos proyectos que hay en la solución.  
  
3.  Elija como destino de la implementación uno de los perfiles de VS Emulator Android Phone (x86).  
  
     Si ha instalado otros emuladores o ha conectado un dispositivo Android, puede elegirlos en la lista desplegable de destinos de implementación.  
  
4.  Presione F5 para iniciar la depuración o Mayús+F5 para iniciar sin depurar.  
  
     Este es el aspecto de la aplicación predeterminada en el emulador de Visual Studio para Android.  
  
     ![El emulador ejecutando la aplicación](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio inicia el emulador, que tarda unos segundos en cargarse e implementar el código. Cuando la aplicación se inicia, puede establecer puntos de interrupción y usar el depurador para ver el código, examinar los locales e inspeccionar los valores.  
  
5.  Presione Mayús+F5 para detener la depuración.  
  
     El emulador es un proceso independiente que sigue ejecutándose. Puede editar, compilar e implementar el código varias veces en el mismo emulador.

