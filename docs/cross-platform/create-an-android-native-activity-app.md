---
title: Crear una aplicación de actividad nativa de Android | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2b8fbc8d651536c35ee2dae985876f38336c9061
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588911"
---
# <a name="create-an-android-native-activity-app"></a>Crear una aplicación de Android Native Activity

Cuando se instala la carga multiplataforma **Desarrollo móvil con C++** , Visual Studio puede usarse para crear aplicaciones native-activity para Android completamente funcionales. El kit de desarrollo nativo (NDK) de Android es un conjunto de herramientas que le permite implementar la mayor parte de su aplicación para Android mediante código de C/C++ puro. El código Java JNI actúa como adherencia para permitir que el código C/C++ interactúe con Android. El NDK de Android introdujo la capacidad para crear aplicaciones Native Activity con la API de Android Level 9. El código Native Activity se usa para crear aplicaciones de juegos y gráficos avanzados que usan Unreal Engine u OpenGL. Este tema le guiará en el proceso de creación de una aplicación Native Activity sencilla que usa OpenGL. Existen temas adicionales que abordan el ciclo de vida de desarrollador al completo incluida la edición, la compilación, la depuración y la implementación de código Native Activity.

## <a name="requirements"></a>Requisitos

Antes de crear una aplicación native-activity para Android, debe asegúrese de que cumple todos los requisitos del sistema y de que tiene instalada la carga de trabajo **Desarrollo móvil con C++** en Visual Studio. Para más información, consulte [Instalación del desarrollo móvil multiplataforma con C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Asegúrese de que las herramientas de terceros y los SDK necesarios estén incluidos en la instalación y que está instalado un emulador para Android.

## <a name="create-a-new-native-activity-project"></a>Crear un nuevo proyecto de Native Activity

En este tutorial, primero debe crear un nuevo proyecto native-activity para Android y, después, compilar y ejecutar la aplicación predeterminada en un emulador para Android.

::: moniker range="vs-2017"

1. En Visual Studio, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Nuevo proyecto**, en **Plantillas**, elija **Visual C++** > **Multiplataforma** y luego elija la plantilla **Aplicación native-activity (Android)** .

1. Ponga a la aplicación un nombre como *MyAndroidApp* y luego elija **Aceptar**.

   ![Cree un proyecto native-activity](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")

   Visual Studio crea la solución nueva y abre el Explorador de soluciones.

   ![Proyecto native-activity en el Explorador de soluciones](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")

::: moniker-end

::: moniker range=">=vs-2019"

1. En Visual Studio, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **Crear un nuevo proyecto**, seleccione la plantilla **Aplicación native-activity (Android)**  y luego elija **Siguiente**.

1. En el cuadro de diálogo **Configurar el nuevo proyecto**, escriba un nombre como *MyAndroidApp* en **Nombre del proyecto** y luego elija **Crear**.

   Visual Studio crea la solución nueva y abre el Explorador de soluciones.

::: moniker-end

La nueva solución de aplicaciones Native Activity de Android incluye dos proyectos:

- `MyAndroidApp.NativeActivity` contiene las referencias y el código de adherencia para que su aplicación se ejecute como Native Activity en Android. La implementación de los puntos de entrada del código de adherencia está en *main.cpp*. Los encabezados precompilados están en *pch.h*. Su proyecto de aplicación de Native Activity se compila en un archivo de biblioteca compartida *.so* que selecciona el proyecto Packaging.

- `MyAndroidApp.Packaging` crea el archivo *.apk* para la implementación en un dispositivo o emulador Android. Este archivo contiene los recursos y el archivo *AndroidManifest.xml* donde se establecen las propiedades del manifiesto. También contiene el archivo *build.xml* que controla el proceso de compilación de Ant. Se establece como proyecto de inicio de manera predeterminada para que se pueda implementar y ejecutar directamente desde Visual Studio.

## <a name="build-and-run-the-default-android-native-activity-app"></a>Compilar y ejecutar la aplicación predeterminada Native Activity de Android

Compile y ejecute la aplicación generada por la plantilla para comprobar su instalación y configuración. Para esta prueba inicial, ejecute la aplicación en uno de los perfiles de dispositivo que instala el emulador para Android. Si prefiere probar la aplicación en otro destino, cargue el emulador de destino o conecte el dispositivo a su equipo.

## <a name="to-build-and-run-the-default-native-activity-app"></a>Para compilar y ejecutar la aplicación Native Activity predeterminada

1. Si aún no está seleccionada, elija la opción **x86** en la lista desplegable **Plataformas de solución** .

     ![Selección de x86 en la lista desplegable Plataformas de solución](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")

     Si la lista **Plataformas de solución** no aparece, seleccione **Plataformas de solución** en la lista **Agregar o quitar botones** y luego seleccione la plataforma.

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

     La ventana Salida muestra la salida del proceso de compilación para los dos proyectos que hay en la solución.

1. Elija como destino de implementación uno de los perfiles del emulador para Android.

     Si ha instalado otros emuladores o ha conectado un dispositivo Android, puede elegirlos en la lista desplegable de destinos de implementación.

1. Presione **F5** para iniciar la depuración o **Mayús**+**F5** para iniciar sin depurar.

   Este es el aspecto de la aplicación predeterminada en un emulador para Android.

   ![El emulador ejecutando la aplicación](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")

   Visual Studio inicia el emulador, que tarda unos segundos en cargarse e implementar el código. Cuando la aplicación se inicia, puede establecer puntos de interrupción y usar el depurador para ver el código, examinar los locales e inspeccionar los valores.

1. Presione **MAYÚS**+**F5** para detener la depuración.

   El emulador es un proceso independiente que sigue ejecutándose. Puede editar, compilar e implementar el código varias veces en el mismo emulador.
