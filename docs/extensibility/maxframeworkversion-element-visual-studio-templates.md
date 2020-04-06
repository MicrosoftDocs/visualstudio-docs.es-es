---
title: MaxFrameworkVersion (Elemento) (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702624"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (plantillas de Visual Studio)

Especifica la versión máxima de .NET Framework que requiere la plantilla. Determina el valor más alto disponible en la lista desplegable **Versión** de marco de trabajo de destino del cuadro de diálogo **Nuevo proyecto.** Para que los usuarios puedan seleccionar una versión de framework, también debe especificar [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) como la versión mínima de .NET Framework para la plantilla.

> [!IMPORTANT]
> A partir de Visual Studio 2017 versión 15.6, la lista desplegable **Versión** de marco de trabajo de destino ya no es un filtro para las plantillas mostradas en la sección **Plantillas** del cuadro de diálogo **Nuevo proyecto.** En su lugar, la lista desplegable **Versión** de marco de trabajo de destino funciona como un selector de marco de trabajo para la plantilla seleccionada.

 \<VSTemplate \<> TemplateData> \<> MaxFrameworkVersion

## <a name="syntax"></a>Sintaxis

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o Agregar **nuevo elemento.**|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el número de versión más alto de .NET Framework permitido por la plantilla.

## <a name="remarks"></a>Observaciones

`MaxFrameworkVersion` es un elemento opcional. El `MaxFrameworkVersion` elemento debe omitirse a menos que sea necesario, para no limitar inadvertidamente el intervalo admitido de versiones de .NET Framework para la plantilla. También debe omitirse si .NET Framework no es aplicable a la plantilla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] muestran los metadatos de una plantilla de clase estándar.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

En este ejemplo, la versión máxima de .NET Framework que `MaxFrameworkVersion`requiere la plantilla, representada por , es 4.7.1. Un proyecto creado con esta plantilla puede tener como destino versiones de .NET Framework hasta 4.7.1.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
