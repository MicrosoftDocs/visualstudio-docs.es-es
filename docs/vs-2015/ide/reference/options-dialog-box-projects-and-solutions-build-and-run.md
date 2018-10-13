---
title: Cuadro de diálogo Opciones, Proyectos y soluciones, Compilación y ejecución | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9669437ff47bc141c898a61c055b3a0de8d5d235
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189298"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
En este cuadro de diálogo puede especificar el número máximo de proyectos de Visual C++ o Visual C# que se pueden compilar al mismo tiempo, determinados comportamientos de compilación predeterminados y algunos ajustes de registro de compilación. Para abrir el **opciones** diálogo cuadro, elija **herramientas**, **opciones** en la barra de menús. Para obtener acceso a este conjunto de opciones, expanda **proyectos y soluciones**y, a continuación, elija **compilar y ejecutar**.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **número máximo de compilaciones de proyecto paralelas**  
 Especifica el número máximo de proyectos de Visual C++ y Visual C# que se pueden compilar al mismo tiempo. Para optimizar el proceso de compilación, el número máximo de compilaciones de proyecto paralelas se establece automáticamente en el número de CPU que tenga el equipo. El máximo es 32.  
  
 **Compilar proyectos de inicio y dependencias únicamente al ejecutar**  
 Solo el proyecto de inicio y sus dependencias se generan si se selecciona esta casilla de verificación cuando se elige la tecla F5; Elija **depurar**, **iniciar** en el menú de barras; o elija **compilar**, **compilar** en la barra de menús. Todos los proyectos, dependencias y archivos de solución se compilan si se desactiva esta casilla de verificación cuando se elige la tecla F5; Elija **depurar**, **iniciar** en el menú de barras; o elija **compilar**, **compilar** en la barra de menús. Esta opción se encuentra desactivada de forma predeterminada.  
  
 **Al ejecutar, cuando los proyectos no estén actualizados**  
 > [!NOTE]
>  Esta lista solo se aplica a proyectos de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 De forma predeterminada, aparece un mensaje si es una configuración de proyecto no actualizada cuando se presione la tecla F5 o elija **depurar**, **iniciar** en la barra de menús. Puede especificar si se debe compilar el proyecto de todos modos y si aparece el mensaje. Utilice esta opción para especificar si aparece el mensaje y cuál debería ser el comportamiento de compilación en caso de que no aparezca el mensaje.  
  
 **Compilar siempre**  
 No aparece el cuadro de mensaje y se compila el proyecto a pesar de que la configuración no está actualizada. Esta opción se establece cuando se selecciona el **no mostrar de nuevo este cuadro de diálogo** en el mensaje y, a continuación, elija el **Sí** botón.  
  
 **No compilar nunca**  
 No aparece el cuadro de mensaje y no se compila el proyecto. Esta opción se establece cuando se selecciona el **no mostrar de nuevo este cuadro de diálogo** en el mensaje y, a continuación, elija el **n** botón.  
  
 **Símbolo del sistema de compilación**  
 Muestra el cuadro de mensaje cada vez que una configuración de proyecto no está actualizada.  
  
 **Al ejecutar, cuando se produzcan errores de compilación o implementación**  
 Si se producen errores de compilación cuando se inicia una compilación desde el **compilar** menú, aparece un mensaje. Puede especificar si desea proceder a iniciar la aplicación y si aparece el mensaje cada vez que se producen errores de compilación. Utilice esta opción para especificar si aparece el mensaje y cuál debería ser el comportamiento en caso de que no aparezca el mensaje.  
  
> [!NOTE]
>  Esta opción solo es aplicable a proyectos de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 **Preguntar al iniciar**  
 Muestra un cuadro de mensaje cada vez que se producen errores de compilación.  
  
 **No iniciar**  
 No aparece el cuadro de mensaje y no se inicia la aplicación. Esta opción se establece cuando se selecciona el **no mostrar de nuevo este cuadro de diálogo** casilla de verificación en el cuadro de mensaje y, a continuación, elija el **n** botón.  
  
 **Iniciar versión antigua**  
 No aparece el cuadro de mensaje y no se inicia la versión recién compilada de la aplicación. Esta opción se establece cuando se selecciona el **no mostrar de nuevo este cuadro de diálogo** casilla de verificación en el cuadro de mensaje y, a continuación, elija el **Sí** botón.  
  
 **Para soluciones nuevas, usar el proyecto seleccionado actualmente como proyecto de inicio**  
 Si se selecciona esta casilla, las nuevas soluciones utilizan el proyecto seleccionado actualmente como proyecto de inicio.  
  
 **Detalles de la salida de la compilación del proyecto de MSBuild**  
 Determina cuánta información aparece en la ventana **Salida** de la compilación.  
  
 **Contenido del archivo de registro de compilación del proyecto de MSBuild**  
 > [!NOTE]
>  Esta opción solo es aplicable a proyectos de Visual C++.  
  
 Determina cuánta información se escribe en el archivo de registro de compilación, que se encuentra en \\...\\*NombreProyecto*\Debug\\*NombreProyecto*.log.  
  
## <a name="see-also"></a>Vea también  
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)



