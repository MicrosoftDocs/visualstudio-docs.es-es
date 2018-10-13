---
title: Tareas de MSBuild específicas de Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da9bdb5c181c9fd935987d629f08af1505f0501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246160"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Tareas de MSBuild específicas de Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Las tareas proporcionan el código que se ejecuta durante el proceso de compilación. Cuando se instala Visual C++, las tareas siguientes están disponibles, además de las que se instalan con [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Para obtener más información, consulte [Información general sobre MSBuild (Visual C++)](http://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Además de los parámetros específicos de cada tarea, las tareas también tienen los parámetros siguientes.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Condition`|Parámetro `String` opcional.<br /><br /> Expresión de tipo `Boolean` que el motor de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] emplea para determinar si se ejecutará esta tarea. Para obtener información sobre las condiciones admitidas en [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], vea [Condiciones](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Parámetro opcional. Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.<br /><br /> Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.<br /><br /> Para obtener más información, consulte [Cómo: Pasar errores por alto en las tareas](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
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



