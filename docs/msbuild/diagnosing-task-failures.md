---
title: Diagnóstico de errores de tareas | Microsoft Docs
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593283"
---
# <a name="diagnosing-task-failures"></a>Diagnóstico de errores de tareas

`MSB6006` se emite cuando una clase derivada de <xref:Microsoft.Build.Utilities.ToolTask> ejecuta un proceso de herramienta que devuelve un código de salida distinto de cero si la tarea no ha registrado un error más específico.

## <a name="identifying-the-failing-task"></a>Identificación de la tarea con error

Cuando se produce un error de tarea, el primer paso es identificar la tarea que tiene errores.

El texto del error especifica el nombre de la herramienta (un nombre descriptivo proporcionado por la implementación de la tarea de <xref:Microsoft.Build.Utilities.ToolTask.ToolName> o el nombre del ejecutable) y el código de salida numérico. Por ejemplo, en:

```text
error MSB6006: "custom tool" exited with code 1.
```

El nombre de la herramienta es `custom tool` y el código de salida es `1`.

### <a name="command-line-builds"></a>Compilaciones de línea de comandos

Si la compilación se configuró para incluir un resumen (el valor predeterminado), el resumen tendrá el siguiente aspecto:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Este resultado indica que el error se produjo en una tarea definida en la línea 19 del archivo `S:\MSB6006_demo\MSB6006_demo.csproj`, en un destino denominado `InvokeToolTask`, en el proyecto `S:\MSB6006_demo\MSB6006_demo.csproj`.

### <a name="in-visual-studio"></a>En Visual Studio

La misma información está disponible en la lista de errores de Visual Studio en las columnas `Project`, `File` y `Line`.

## <a name="finding-more-failure-information"></a>Búsqueda de más información sobre el error

Este error se emite cuando la tarea no registra un error específico. El no poder registrar un error suele deberse a que la tarea no está configurada para comprender el formato de error emitido por la herramienta a la que llama.

En general, las herramientas que se comportan correctamente emiten información contextual o de error a su salida estándar o flujo de error, y las tareas capturan y registran esta información de forma predeterminada. Para más información, examine las entradas de registro anteriores a la aparición del error. Puede que sea necesario volver a ejecutar la compilación con un nivel de registro superior para conservar esta información.

## <a name="next-steps"></a>Pasos siguientes

Afortunadamente, el contexto o los errores adicionales identificados en el registro revelan la causa principal del problema.

Si no es así, puede que deba examinar las propiedades y los elementos que son entradas a la tarea con error para delimitar las causas posibles.
