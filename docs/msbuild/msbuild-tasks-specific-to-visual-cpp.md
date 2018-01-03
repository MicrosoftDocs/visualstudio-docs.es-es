---
title: "Tareas de MSBuild específicas de Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords: MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e725bc94a159ea5295341021f60ee1183a8982e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Tareas de MSBuild específicas de Visual C++
Las tareas proporcionan el código que se ejecuta durante el proceso de compilación. Cuando se instala Visual C++, las tareas siguientes están disponibles, además de las que se instalan con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Para obtener más información, consulte [Información general sobre MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview).  
  
 Además de los parámetros específicos de cada tarea, las tareas también tienen los parámetros siguientes.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`Condition`|Parámetro `String` opcional.<br /><br /> Expresión de tipo `Boolean` que el motor de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] emplea para determinar si se ejecutará esta tarea. Para obtener información sobre las condiciones admitidas en [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vea [Condiciones](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parámetro opcional. Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.<br /><br /> Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.<br /><br /> Para obtener más información, consulte [Cómo: Pasar errores por alto en las tareas](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Description|  
|-----------|-----------------|  
|[Tarea BscMake](../msbuild/bscmake-task.md)|Ajusta la herramienta Utilidad de mantenimiento de información de examen de Microsoft (bscmake.exe).|  
|[Tarea CL](../msbuild/cl-task.md)|Incluye la herramienta compilador de Visual C++, cl.exe.|  
|[Tarea CPPClean](../msbuild/cppclean-task.md)|Elimina los archivos temporales que MSBuild crea cuando se compila un proyecto de Visual C++.|  
|[Tarea LIB](../msbuild/lib-task.md)|Incluye la herramienta Administrador de bibliotecas de 32 bits de Microsoft (lib.exe).|  
|[Vincular tarea](../msbuild/link-task.md)|Incluye la herramienta del vinculador de Visual C++ (link.exe).|  
|[Tarea MIDL](../msbuild/midl-task.md)|Incluye la herramienta de compilación Lenguaje de definición de interfaz de Microsoft (MIDL) (midl.exe).|  
|[Tarea MT](../msbuild/mt-task.md)|Incluye la herramienta Manifiesto de Microsoft (mt.exe).|  
|[Tarea RC](../msbuild/rc-task.md)|Incluye la herramienta Compilador de recursos de Microsoft Windows (rc.exe).|  
|[Tarea SetEnv](../msbuild/setenv-task.md)|Establece o elimina el valor de una variable de entorno especificada.|  
|[Tarea VCMessage](../msbuild/vcmessage-task.md)|Registra mensajes de advertencia y mensajes de error durante una compilación.|  
|[Tarea XDCMake](../msbuild/xdcmake-task.md)|Incluye la herramienta Documentación XML (xdcmake.exe), que combina archivos de comentarios de documento XML (.xdc) en un archivo .xml.|  
|[Tarea XSD](../msbuild/xsd-task.md)|Encapsula la herramienta de definición de esquema XML (xsd.exe), que genera archivos de esquema o clase desde un origen.|  
|[Referencia de MSBuild](../msbuild/msbuild-reference.md)|Describe los elementos del sistema MSBuild.|  
|[Tareas](../msbuild/msbuild-tasks.md)|Describe tareas, que son unidades de código que se pueden combinar para generar una compilación.|  
|[Escribir tareas](../msbuild/task-writing.md)|Describe cómo se crea una tarea.|