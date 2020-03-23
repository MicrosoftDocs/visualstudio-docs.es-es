---
title: XslTransformation (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d23799e5ce5bf391915ac459c69c27b990211f0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094552"
---
# <a name="xsltransformation-task"></a>XslTransformation (tarea)

Transforma una entrada XML mediante una transformación XSL o una transformación XSL compilada y la envía a un dispositivo de salida o archivo.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `XslTransformation` .

|Parámetro|Descripción|
|---------------|-----------------|
|`OutputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos de salida de la transformación XML.|
|`Parameters`|Parámetro `String` opcional.<br /><br /> Especifica los parámetros del documento de entrada XSLT.  Proporcione el XML sin formato que contiene cada parámetro como `<Parameter Name="" Value="" Namespace="" />`.|
|`XmlContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XML como una cadena.|
|`XmlInputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos de entrada XML.|
|`XslCompiledDllPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el XSLT compilado.|
|`XslContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XSLT como una cadena.|
|`XslInputPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el archivo de entrada XSLT.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se usa un archivo *transform.xslt* de transformación XSL para modificar el archivo XML `$(XmlInputFileName)`. El XML transformado se escribe en `$(IntermediateOutputPath)output.xml`. La transformación XSL toma `$(Parameter1)` como un parámetro de entrada.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Vea también

- [Parámetros XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
