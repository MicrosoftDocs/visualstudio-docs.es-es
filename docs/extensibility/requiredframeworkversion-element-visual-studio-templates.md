---
title: RequiredFrameworkVersion (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6490c75f7ca57dbb287da818dacd02574025f00f
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion (Elemento, Plantillas de Visual Studio)

Especifica la versión mínima de .NET Framework que requiere la plantilla. Hace que la **versión de Framework de destino** lista desplegable que se mostrará en el **nuevo proyecto** cuadro de diálogo. El `RequiredFrameworkVersion` elemento determina también el valor más bajo disponible en la lista desplegable.

> [!IMPORTANT]
> A partir de Visual Studio 2017 versión 15.6, el **versión de Framework de destino** dropdown ya no es un filtro para las plantillas que se muestran en la **plantillas** sección de la **nuevo proyecto** cuadro de diálogo. En su lugar, la lista desplegable funciona como un selector de framework para la plantilla seleccionada.

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>Sintaxis

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestran en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el número de versión mínima de .NET Framework que se requiere para la plantilla.

## <a name="remarks"></a>Comentarios

`RequiredFrameworkVersion` es un elemento opcional. Utilice este elemento solo si la plantilla admite una versión mínima específica (y versiones posteriores, si lo hay) de .NET Framework. Si especifica la `RequiredFrameworkVersion` elemento y la plantilla no es compatible con una versión mínima específica de .NET Framework, el **versión de Framework de destino** lista desplegable que se muestra cuando no es aplicable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra los metadatos de un estándar [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla de clase.

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

En este ejemplo, la versión mínima de .NET Framework que requiere la plantilla, representado por `RequiredFrameworkVersion`, es 3.0. Un proyecto creado con esta plantilla puede tener como destino versiones de .NET Framework a partir de 3.0.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
- [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
