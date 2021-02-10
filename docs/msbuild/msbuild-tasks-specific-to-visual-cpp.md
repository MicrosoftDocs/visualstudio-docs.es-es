---
title: Tareas de MSBuild específicas de C++ | Microsoft Docs
description: Vea las tareas de MSBuild que están disponibles cuando C++ está instalado, que MSBuild usa al compilar el código C++.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 82ba5ad3beb8a676df23cc69184c8766bca72f77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878271"
---
# <a name="msbuild-tasks-specific-to-c"></a>Tareas de MSBuild específicas de C++

Las tareas proporcionan el código que se ejecuta durante el proceso de compilación. Cuando se instala C++, las tareas siguientes están disponibles, además de las que se instalan con MSBuild. Para más información, consulte [Información general sobre MSBuild (C++)](/cpp/build/msbuild-visual-cpp-overview).

 Además de los parámetros específicos de cada tarea, las tareas también tienen los parámetros siguientes.

| Parámetro | Descripción |
|-------------------| - |
| `Condition` | Parámetro `String` opcional.<br /><br /> Expresión de tipo `Boolean` que el motor de MSBuild emplea para determinar si se ejecutará esta tarea. Para obtener información sobre las condiciones admitidas en MSBuild, vea [Condiciones](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parámetro opcional. Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.<br /><br /> Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.<br /><br /> Para obtener más información, vea [Cómo: Pasar errores por alto en las tareas](../msbuild/how-to-ignore-errors-in-tasks.md). |

### <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tarea BscMake](../msbuild/bscmake-task.md)|Incluye la herramienta Utilidad de mantenimiento de información de examen de Microsoft (*bscmake.exe*).|
|[CL (tarea)](../msbuild/cl-task.md)|Contiene la herramienta del compilador de C++ (*cl.exe*).|
|[Tarea CPPClean](../msbuild/cppclean-task.md)|Elimina los archivos temporales que MSBuild crea cuando se compila un proyecto de C++.|
|[Tarea ClangCompile](../msbuild/clangcompile-task.md)|Contiene la herramienta del compilador de C++ (*clang.exe*).|
|[Tarea CustomBuild](../msbuild/custombuild-task.md)|Contiene la herramienta del compilador de C++ (*cmd.exe*).|
|[Tarea FXC](../msbuild/fxc-task.md)|Use los compiladores de sombreador de HLS en el proceso de compilación.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|Lee TLog antiguos, escribe TLog nuevos y devuelve un conjunto de elementos no actualizados. (tarea asistente)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|Obtiene el nombre de archivo de salida para cl y otras herramientas, lo que permite especificar solo el directorio de salida, el nombre de archivo completo o nada. (tarea asistente)|
|[LIB (tarea)](../msbuild/lib-task.md)|Incluye la herramienta del Administrador de bibliotecas de Microsoft de 32 bits (*lib.exe*).|
|[Vincular tarea](../msbuild/link-task.md)|Contiene la herramienta del compilador de C++ (*link.exe*).|
|[MIDL (tarea)](../msbuild/midl-task.md)|Incluye la herramienta de compilación Lenguaje de definición de interfaz de Microsoft (MIDL), *midl.exe*.|
|[MT (tarea)](../msbuild/mt-task.md)|Incluye la herramienta Manifiesto de Microsoft (*mt.exe*).|
|[Tarea MultiToolTask](../msbuild/multitooltask-task.md)|Sin descripción.|
|[Tarea ParallelCustomBuild](../msbuild/parallelcustombuild-task.md)|Ejecute instancias en paralelo de la [tarea CustomBuild](../msbuild/custombuild-task.md).|
|[RC (tarea)](../msbuild/rc-task.md)|Incluye la herramienta Compilador de recursos de Microsoft Windows (*rc.exe*).|
|[Tarea SetEnv](../msbuild/setenv-task.md)|Establece o elimina el valor de una variable de entorno especificada.|
|[Clase base TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md)|Se hereda de [VCToolTask](../msbuild/vctooltask-base-class.md).|
|[VCMessage (tarea)](../msbuild/vcmessage-task.md)|Registra mensajes de advertencia y mensajes de error durante una compilación. (No ampliable. Solo para uso interno).|
|[Clase base VCToolTask](../msbuild/vctooltask-base-class.md)|Se hereda de [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask).|
|[XDCMake (tarea)](../msbuild/xdcmake-task.md)|Incluye la herramienta Documentación XML (*xdcmake.exe*), que combina archivos de comentarios de documento XML ( *.xdc*) en un archivo *.xml*.|
|[XSD (tarea)](../msbuild/xsd-task.md)|Encapsula la herramienta de definición de esquema XML (*xsd.exe*), que genera archivos de esquema o clase desde un origen. *Vea la nota siguiente.*|
|[Referencia de MSBuild](../msbuild/msbuild-reference.md)|Describe los elementos del sistema MSBuild.|
|[Tareas](../msbuild/msbuild-tasks.md)|Describe tareas, que son unidades de código que se pueden combinar para generar una compilación.|
|[Escribir tareas](../msbuild/task-writing.md)|Describe cómo se crea una tarea.|

> [!NOTE]
> A partir de Visual Studio 2017, el proyecto C++ ya no es compatible con *xsd.exe*. Puede seguir usando la API **Microsoft.VisualC.CppCodeProvider** agregando manualmente *CppCodeProvider.dll* a la GAC.
