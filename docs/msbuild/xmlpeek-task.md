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
ms.openlocfilehash: 27b535af260d205c74ef87d0325680389d1dbe58
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286126"
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

Con los espacios de nombres XML, se usa el parámetro `Namespaces`, como en el ejemplo siguiente. Con el archivo XML de entrada `XMLFile1.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<class AccessModifier='public' Name='test' xmlns:s='http://nsurl'>
  <s:variable Type='String' Name='a'>This</s:variable>
  <s:variable Type='String' Name='b'>is</s:variable>
  <s:variable Type='String' Name='c'>Sparta!</s:variable>
  <method AccessModifier='public static' Name='GetVal' />
</class>
```

Y el siguiente `Target` definido en un archivo de proyecto:

```xml
  <Target Name="TestPeek" BeforeTargets="Build">
    <!-- Find the Name attributes -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/@Name"
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value1" />
    </XmlPeek>
    <Message Text="@(value1)"/>
    <!-- Find 'variable' nodes (XPath query includes ".") -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/."
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value2" />
    </XmlPeek>
    <Message Text="@(value2)"/>
  </Target>
```

La salida incluye lo siguiente del destino `TestPeek`:

```output
  TestPeek output:
  a;b;c
  <s:variable Type="String" Name="a" xmlns:s="http://nsurl">This</s:variable>;<s:variable Type="String" Name="b" xmlns:s="http://nsurl">is</s:variable>;<s:variable Type="String" Name="c" xmlns:s="http://nsurl">Sparta!</s:variable>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Sintaxis de consulta de XPath](https://wikipedia.org/wiki/XPath)
