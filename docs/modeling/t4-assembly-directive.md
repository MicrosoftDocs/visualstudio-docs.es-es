---
title: Directiva de ensamblado T4
description: Obtenga información sobre que, Visual Studio plantilla de texto en tiempo de diseño, la directiva de ensamblado carga un ensamblado para que el código de plantilla pueda usar sus tipos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 38b5a7fe2308884d4837a068770af67435ada70e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386363"
---
# <a name="t4-assembly-directive"></a>Directiva de ensamblado T4

En una Visual Studio de texto en tiempo de diseño, la directiva carga un ensamblado para que el código de plantilla `assembly` pueda usar sus tipos. El efecto es similar a agregar una referencia de ensamblado en un Visual Studio proyecto.

 Para obtener información general sobre cómo escribir plantillas de texto, vea [Escribir una plantilla de texto T4.](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> No necesita la directiva de salida `assembly` en una plantilla de texto (preprocesada) en tiempo de ejecución. En su lugar, agregue los ensamblados necesarios a **las referencias** del Visual Studio proyecto.

## <a name="using-the-assembly-directive"></a>Usar la directiva de ensamblado
 La sintaxis de las directivas es la siguiente:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 El nombre del ensamblado debe ser uno de los siguientes:

- El nombre seguro de un ensamblado en la GAC, como `System.Xml.dll`. También puede utilizar el formulario largo, como `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Para más información, consulte <xref:System.Reflection.AssemblyName>.

- La ruta de acceso absoluta del ensamblado

  Puede usar la `$(variableName)` sintaxis para hacer referencia a Visual Studio variables como `$(SolutionDir)` , y para hacer referencia a variables de `%VariableName%` entorno. Por ejemplo:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 La directiva de ensamblado no tiene ningún efecto en una plantilla de texto preprocesada. En su lugar, incluya las referencias necesarias en la **sección Referencias** del Visual Studio proyecto. Para obtener más información, vea [Generación de texto en tiempo de ejecución con plantillas de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Ensamblados estándar
 Loa siguientes ensamblados se cargan automáticamente, por lo que no es necesario escribir las directivas de ensamblado para ellos:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Si utiliza una directiva personalizada, el procesador de directivas podría cargar ensamblados adicionales. Por ejemplo, si escribe plantillas para un lenguaje específico del dominio (ADSL), no necesita escribir directivas de ensamblado para los siguientes ensamblados:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- El ensamblado contiene el ADSL.

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> Uso de propiedades de proyecto en MSBuild y Visual Studio
 Visual Studio macros como $(SolutionDir) no funcionan en MSBuild. Si desea transformar plantillas del equipo de compilación, tiene que utilizar las propiedades del proyecto.

 Modifique el archivo .csproj o .vbproj para definir una propiedad de proyecto. En este ejemplo se define una propiedad denominada `myLibFolder`:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Ahora puede utilizar la propiedad del proyecto en plantillas de texto, que se transformarán correctamente en Visual Studio y MSBuild:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Vea también

- [Directiva Include T4](../modeling/t4-include-directive.md)
