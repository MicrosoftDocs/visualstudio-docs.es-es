---
title: Tarea XmlPeek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094669"
---
# <a name="xmlpeek-task"></a>XmlPeek (tarea)

Devuelve valores conforme a lo que especifica una consulta XPath de un archivo XML.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `XmlPeek` .

|Parámetro|Descripción|
|---------------|-----------------|
|`Namespaces`|Parámetro `String` opcional.<br /><br /> Especifica los espacios de nombres para los prefijos de la consulta XPath.|
|`Query`|Parámetro `String` opcional.<br /><br /> Especifica la consulta XPath.|
|`Result`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los resultados que devuelve esta tarea.|
|`XmlContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XML como una cadena.|
|`XmlInputPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la entrada XML como una ruta de acceso a archivo.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).



## <a name="example"></a>Ejemplo

Esto es un archivo XML `settings.config` de ejemplo para leer:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

En este ejemplo, si quiere leer `value`, use un código similar al siguiente:

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
