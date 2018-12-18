---
title: Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b2d047201214e3a7cd4c14c61baa041840decd8
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143325"
---
# <a name="options-dialog-box-projects-and-solutions-build-and-run"></a>Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar

En este cuadro de diálogo puede especificar el número máximo de proyectos de Visual C++ o C# que se pueden compilar al mismo tiempo, determinados comportamientos de compilación predeterminados y algunos ajustes de registro de compilación. Para acceder a estas opciones, seleccione **Herramientas > Opciones**, expanda **Proyectos y soluciones** y elija **Compilación y ejecución**.

**Número máximo de compilaciones de proyecto paralelas**

Especifica el número máximo de proyectos de Visual C++ y C# que se pueden compilar al mismo tiempo. Para optimizar el proceso de compilación, el número máximo de compilaciones de proyecto paralelas se establece automáticamente en el número de CPU que tenga el equipo. El máximo es 32.

**Compilar proyectos de inicio y dependencias únicamente al ejecutar**

Compila solo el proyecto de inicio y sus dependencias cuando se usa la tecla F5 y se selecciona el comando de menú **Depurar &gt; Iniciar** o comandos aplicables en el menú **Compilar**. Si está desactivado, se compilan todos los proyectos y las dependencias.

**Al ejecutar, cuando los proyectos no estén actualizados**

*Solo es aplicable a proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Cuando se ejecuta un proyecto con F5 o el comando **Depurar > Iniciar**, la opción predeterminada **Preguntar si se compila** muestra un mensaje si una configuración de proyecto no está actualizada. Seleccione **Compilar siempre** para compilar el proyecto cada vez que se ejecute. Seleccione **No compilar nunca** para suprimir todas las compilaciones automáticas cuando se ejecute un proyecto.

**Al ejecutar, cuando se produzcan errores de compilación o implementación**

*Solo es aplicable a proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Cuando se ejecuta un proyecto con F5 o el comando **Depurar > Iniciar**, la opción predeterminada **Preguntar al iniciar** muestra un mensaje si se debe ejecutar un proyecto incluso si se produjo un error en la compilación. Seleccione **Iniciar versión antigua** para iniciar automáticamente la última compilación correcta, lo que podría dar lugar a discrepancias entre el código en ejecución y el código fuente. Seleccione **No iniciar** para suprimir el mensaje.

**Para soluciones nuevas, usar el proyecto seleccionado actualmente como proyecto de inicio**

Cuando se establece esta opción, las soluciones nuevas usan el proyecto seleccionado actualmente como proyecto de inicio.

**Detalles de la salida de la compilación del proyecto de MSBuild**

Determina cuánta información aparece en la ventana **Salida** de la compilación.

**Contenido del archivo de registro de compilación del proyecto de MSBuild**

*Solo es aplicable a proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].*

Determina cuánta información se escribe en el archivo de registro de compilación, que se encuentra en \\...\\*NombreProyecto*\Debug\\*NombreProyecto*.log.

## <a name="see-also"></a>Vea también

- [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones](projects-and-solutions-options-dialog-box.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones, Proyectos web](options-dialog-box-projects-and-solutions-web-projects.md)