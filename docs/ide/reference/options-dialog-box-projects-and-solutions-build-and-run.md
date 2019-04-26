---
title: Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar
ms.date: 07/14/2017
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d0f24dc1afa875183f03e15e46cc2331f27cbf0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996839"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>Cuadro de diálogo Opciones: Proyectos y soluciones \> Compilar y ejecutar

En este cuadro de diálogo puede especificar el número máximo de proyectos de C++ o C# que se pueden compilar al mismo tiempo, determinados comportamientos de compilación predeterminados y algunos ajustes de registro de compilación. Para acceder a estas opciones, seleccione **Herramientas** > **Opciones**, expanda **Proyectos y soluciones** y seleccione **Build and Run** (Compilar y ejecutar).

**Número máximo de compilaciones de proyecto paralelas**

Especifica el número máximo de proyectos de C++ y C# que se pueden compilar al mismo tiempo. Para optimizar el proceso de compilación, el número máximo de compilaciones de proyecto paralelas se establece automáticamente en el número de CPU que tenga el equipo. El máximo es 32.

**Compilar proyectos de inicio y dependencias únicamente al ejecutar**

Compila solo el proyecto de inicio y sus dependencias cuando se usa la tecla **F5**, el comando de menú **Depurar** > **Iniciar depuración** o comandos aplicables en el menú **Compilar**. Si está desactivado, se compilan todos los proyectos y las dependencias.

**Al ejecutar, cuando los proyectos no estén actualizados**

*Solo se aplica a proyectos de C++*.

Cuando se ejecuta un proyecto con **F5** o el comando **Depurar** > **Iniciar depuración**, la opción predeterminada **Preguntar si se compila** muestra un mensaje si una configuración de proyecto no está actualizada. Seleccione **Compilar siempre** para compilar el proyecto cada vez que se ejecute. Seleccione **No compilar nunca** para suprimir todas las compilaciones automáticas cuando se ejecute un proyecto.

**Al ejecutar, cuando se produzcan errores de compilación o implementación**

*Solo se aplica a proyectos de C++*.

Cuando se ejecuta un proyecto con **F5** o el comando **Depurar** > **Iniciar depuración**, la opción predeterminada **Preguntar al iniciar** muestra un mensaje si se debe ejecutar un proyecto incluso si se produjo un error en la compilación. Seleccione **Iniciar versión antigua** para iniciar automáticamente la última compilación correcta, lo que podría dar lugar a discrepancias entre el código en ejecución y el código fuente. Seleccione **No iniciar** para suprimir el mensaje.

**Para soluciones nuevas, usar el proyecto seleccionado actualmente como proyecto de inicio**

Cuando se establece esta opción, las soluciones nuevas usan el proyecto seleccionado actualmente como proyecto de inicio.

**Detalles de la salida de la compilación del proyecto de MSBuild**

Determina la cantidad de información del proceso de compilación que se muestra en la ventana de **salida**.

**Contenido del archivo de registro de compilación del proyecto de MSBuild**

*Solo se aplica a proyectos de C++*.

Determina la cantidad de información que se escribe en el archivo de registro de compilación, que se encuentra en *\\\<NombreProyecto>\Debug\\\<NombreProyecto>.log*.

## <a name="see-also"></a>Vea también

- [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones](projects-and-solutions-options-dialog-box.md)
- [Cuadro de diálogo Opciones, Proyectos y soluciones, Proyectos web](options-dialog-box-projects-and-solutions-web-projects.md)