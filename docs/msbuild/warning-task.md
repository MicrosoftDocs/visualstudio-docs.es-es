---
title: Warning (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea Warning para registrar una advertencia durante una compilación basándose en una instrucción condicional evaluada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce7104c08ce8f18672bf4d2df93debc3c1d19983
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047822"
---
# <a name="warning-task"></a>Warning (tarea)

Registra una advertencia durante la compilación basándose en una instrucción condicional evaluada.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `Warning` .

| Parámetro | Description |
|---------------| - |
| `Code` | Parámetro `String` opcional.<br /><br /> Código de advertencia que se debe asociar a la advertencia. |
| `File` | Parámetro `String` opcional.<br /><br /> Especifica el archivo correspondiente, si existe. Si no se proporciona ningún archivo, se utiliza el archivo que contiene la tarea Warning. |
| `HelpKeyword` | Parámetro `String` opcional.<br /><br /> Palabra clave de ayuda que se debe asociar a la advertencia. |
| `Text` | Parámetro `String` opcional.<br /><br /> Texto de advertencia que registra MSBuild si el parámetro `Condition` se evalúa como `true`. |

## <a name="remarks"></a>Comentarios

 La tarea `Warning` permite que los proyectos de MSBuild verifiquen la presencia de una configuración o una propiedad necesaria antes de continuar con el siguiente paso de compilación.

 Si el parámetro `Condition` de la tarea `Warning` se evalúa como `true`, se registra el valor del parámetro `Text` y la compilación continúa ejecutándose. Si no existe ningún parámetro `Condition`, se registra el texto de advertencia. Para obtener más información sobre los registros, vea [Obtener registros de compilación con MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

 En el ejemplo de código siguiente se verifican las propiedades que se establecen en la línea de comandos. Si no se establece ninguna propiedad, el proyecto genera un evento de advertencia y registra el valor del parámetro `Text` de la tarea `Warning`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Consulte también

- [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
