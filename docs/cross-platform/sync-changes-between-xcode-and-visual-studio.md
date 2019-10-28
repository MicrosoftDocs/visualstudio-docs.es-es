---
title: Sincronización de cambios entre Xcode y Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xamarin
ms.openlocfilehash: 5d7d7fab8080028da0ca906b0e75ddf2bf0f1f8c
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589120"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Sincronización de cambios entre Xcode y Visual Studio

Los componentes de desarrollo móvil con C++ en Visual Studio incluyen funcionalidades remotas para sincronizar el trabajo entre su PC y el equipo Mac. Cuando el equipo Mac y el equipo con Visual Studio están emparejados, existen opciones nuevas para proyectos de aplicación de iOS en Visual Studio que puede usar para abrir el proyecto en Xcode, mover el código entre Xcode y Visual Studio, y limpiar el directorio temporal del proyecto de Xcode.

Para usar las opciones de equipo remoto, el proyecto debe ser un proyecto de aplicación de iOS y Visual Studio debe estar emparejado con el equipo Mac. Para ver los requisitos previos y las instrucciones sobre cómo emparejar un equipo Mac, vea [Instalar y configurar herramientas para compilar con iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>El menú Equipo remoto

En el **Explorador de soluciones**, haga clic con el botón derecho en un proyecto de aplicación de iOS para mostrar el menú contextual. Seleccione el elemento **Equipo remoto** para mostrar las opciones remotas disponibles.

![El elemento de menú Equipo remoto en el Explorador de soluciones](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

Estos comandos permiten abrir el proyecto en Xcode, mover los cambios locales o todo el proyecto entre Visual Studio y Xcode, y limpiar los archivos temporales en el equipo remoto.

## <a name="open-in-xcode"></a>Abrir en Xcode

Para abrir el proyecto en Xcode desde Visual Studio, en el submenú **Equipo remoto**, seleccione **Abrir en Xcode** para abrir el proyecto seleccionado en el equipo remoto emparejado. El servidor de `vcremote` se usa para abrir Xcode en el Mac y navegar hasta el directorio temporal creado en el Mac que contiene una copia del proyecto. Visual Studio abre un cuadro de diálogo que muestra el directorio temporal usado para el proyecto. En la ventana **Salida** de Visual Studio también se muestran las acciones realizadas en el equipo remoto. Para verlas, puede que necesite seleccionar **Máquina remota de Visual C++** en la lista desplegable **Mostrar salida de** en la parte superior de la ventana **Salida**.

![La ventana Salida muestra las acciones del equipo remoto.](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")

En el equipo Mac, puede usar todas las herramientas de Xcode para editar el código y los recursos, los guiones gráficos y las acciones. En Visual Studio, el proyecto de aplicación de iOS se anota con "Abierta en Xcode" para indicar que se pueden realizar cambios en el equipo remoto. Una vez completados los cambios, puede usar los comandos Extraer de equipo remoto o Extracción incremental de equipo remoto para volver a copiar los cambios en el proyecto de Visual Studio.

## <a name="push-to-remote-and-incremental-push-to-remote"></a>Insertar en equipo remoto e Inserción incremental en equipo remoto

Si realizó cambios en el proyecto de aplicación de iOS en Visual Studio, los comandos Insertar en equipo remoto e Inserción incremental en equipo remoto pueden usarse para mover los archivos de proyecto modificados al equipo remoto emparejado. El comando Insertar en equipo remoto copia todos los archivos de proyecto en el equipo remoto. El comando Inserción incremental en equipo remoto solo copia los archivos cambiados en el equipo remoto. Para proyectos grandes con pequeños cambios, el comando incremental puede ahorrar tiempo y ancho de banda.

Para copiar los archivos del proyecto en el equipo Mac, en **Explorador de soluciones** de Visual Studio, haga clic con el botón derecho en el proyecto de aplicación de iOS para abrir el menú contextual. Seleccione **Equipo remoto** y elija **Insertar en equipo remoto** o **Inserción incremental en equipo remoto** para copiar los archivos de proyecto desde Visual Studio al equipo Mac.

## <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Extraer de equipo remoto y Extracción incremental de equipo remoto

Después de realizar los cambios en el proyecto en Xcode, mueva de nuevo los cambios a Visual Studio para mantener sincronizados los proyectos.

Para copiar los archivos del proyecto desde el equipo Mac, en **Explorador de soluciones** de Visual Studio, haga clic con el botón derecho en el proyecto de aplicación de iOS para abrir el menú contextual. Seleccione **Equipo remoto** y elija **Extraer de equipo remoto** o **Extracción incremental de equipo remoto** para copiar los archivos de proyecto desde el equipo Mac a Visual Studio.

## <a name="clean-remote"></a>Limpiar equipo remoto

Puede usar el comando Limpiar equipo remoto para eliminar los archivos en el directorio de proyecto temporal en el equipo remoto. El contenido del directorio, incluidos los archivos de código fuente o productos de compilación, se eliminan del equipo Mac. Antes de usar el comando Limpiar equipo remoto, asegúrese de que sincronizó los cambios que quiere mantener en Visual Studio mediante Extraer de equipo remoto o Extracción incremental de equipo remoto.

Para limpiar el directorio de proyecto temporal en el equipo remoto, en **Explorador de soluciones** de Visual Studio, haga clic con el botón derecho en el proyecto de aplicación de iOS para abrir el menú contextual. Seleccione **Equipo remoto** y elija **Limpiar equipo remoto** para quitar los archivos del directorio de proyecto del equipo Mac.
