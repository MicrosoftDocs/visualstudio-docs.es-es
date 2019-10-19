---
title: Cuadro de diálogo Opciones, Proyectos y soluciones, Compilación y ejecución | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655187"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este cuadro de diálogo puede especificar el número máximo de proyectos de Visual C++ o Visual C# que se pueden compilar al mismo tiempo, determinados comportamientos de compilación predeterminados y algunos ajustes de registro de compilación. Para abrir el cuadro de diálogo **Opciones**, seleccione **Herramientas**, **Opciones** en la barra de menús. Para acceder a este conjunto de opciones, expanda **Proyectos y soluciones** y, después, haga clic en **Compilar y ejecutar**.

## <a name="uielement-list"></a>Lista de UIElement
 **número máximo de compilaciones de proyecto paralelas** Especifica el número máximo de proyectos C++ visuales y C# visuales que se pueden compilar al mismo tiempo. Para optimizar el proceso de compilación, el número máximo de compilaciones de proyecto paralelas se establece automáticamente en el número de CPU que tenga el equipo. El máximo es 32.

 **Solo compilar proyectos de inicio y dependencias en ejecución** Cuando se selecciona la tecla F5, solo se compilan el proyecto de inicio y sus dependencias. elija **depurar**, **iniciar** en la barra de menús. o bien, elija **compilar**, **compilar** en la barra de menús. Si esta casilla está desactivada al presionar la tecla F5, se compilan todos los proyectos, dependencias y archivos de la solución; en la barra de menús, seleccione **Depurar**, **Iniciar**, o bien **Compilar**,  **Compilar**. Esta opción se encuentra desactivada de forma predeterminada.

 **Al ejecutar, cuando los proyectos no estén actualizados**
 > [!NOTE]
> Esta lista solo se aplica a proyectos de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 De forma predeterminada, aparece un mensaje si una configuración de proyecto no está actualizada al presionar la tecla F5 o seleccionar **Depurar**, **Iniciar** en la barra de menús. Puede especificar si se debe compilar el proyecto de todos modos y si aparece el mensaje. Utilice esta opción para especificar si aparece el mensaje y cuál debería ser el comportamiento de compilación en caso de que no aparezca el mensaje.

 **Compilar siempre** No aparece el cuadro de mensaje y el proyecto se compila a pesar de la configuración no actualizada. Esta opción se establece cuando se activa la casilla **No volver a mostrar este cuadro de diálogo** y, después, se hace clic en el botón **Sí**.

 No **compilar nunca** No aparece el cuadro de mensaje y no se compila el proyecto. Esta opción se establece cuando se activa la casilla **No volver a mostrar este cuadro de diálogo** y, después, se hace clic en el botón **No**.

 **Preguntar para compilar** Muestra el cuadro de mensaje cada vez que una configuración de proyecto no está actualizada.

 **Al ejecutar, cuando se producen errores de compilación o implementación** Si se producen errores de compilación al iniciar una compilación desde el menú **compilar** , aparece un mensaje. Puede especificar si desea proceder a iniciar la aplicación y si aparece el mensaje cada vez que se producen errores de compilación. Utilice esta opción para especificar si aparece el mensaje y cuál debería ser el comportamiento en caso de que no aparezca el mensaje.

> [!NOTE]
> Esta opción solo es aplicable a proyectos de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 **Preguntar al iniciar** Muestra un cuadro de mensaje cada vez que se producen errores de compilación.

 **No iniciar** No aparece el cuadro de mensaje y no se inicia la aplicación. Esta opción se establece cuando se activa la casilla **No volver a mostrar este cuadro de diálogo** y, después, se hace clic en el botón **No**.

 **Iniciar versión anterior** No aparece el cuadro de mensaje y no se inicia la versión recién compilada de la aplicación. Esta opción se establece cuando se activa la casilla **No volver a mostrar este cuadro de diálogo** y, después, se hace clic en el botón **Sí**.

 **En el caso de las nuevas soluciones, use el proyecto seleccionado actualmente como proyecto de inicio** . Si esta casilla está activada, las nuevas soluciones usan el proyecto seleccionado actualmente como proyecto de inicio.

 **Detalle** de la salida de compilación del proyecto de MSBuild Determina cuánta información aparece en la ventana de **salida** de la compilación.

 **Contenido del archivo de registro de compilación del proyecto de MSBuild**
 > [!NOTE]
> Esta opción solo es aplicable a proyectos de Visual C++.

 Determina cuánta información se escribe en el archivo de registro de compilación, que se encuentra en \\...\\*NombreProyecto*\Debug\\*NombreProyecto*.log.

## <a name="see-also"></a>Vea también
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)
