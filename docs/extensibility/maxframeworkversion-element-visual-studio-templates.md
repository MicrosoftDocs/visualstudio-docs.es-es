---
title: MaxFrameworkVersion (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: edc3f443423a6c70815c4f32f1b2c91d5ead85b6
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion (Elemento, Plantillas de Visual Studio)

Especifica la versión máxima de .NET Framework que requiere la plantilla. Determina el valor más alto disponible en la **versión de Framework de destino** lista desplegable de la **nuevo proyecto** cuadro de diálogo. En orden para que los usuarios puedan seleccionar una versión de framework, también debe especificar [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) como la versión mínima de .NET Framework para la plantilla.

> [!IMPORTANT]
> A partir de Visual Studio 2017 versión 15.6, el **versión de Framework de destino** dropdown ya no es un filtro para las plantillas que se muestran en la **plantillas** sección de la **nuevo proyecto** cuadro de diálogo. En su lugar, el **versión de Framework de destino** desplegable funciona como un selector de framework para la plantilla seleccionada.

 \<VSTemplate> \<TemplateData> \<MaxFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestran en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el mayor número de versión de .NET Framework que está permitido por la plantilla.

## <a name="remarks"></a>Comentarios

`MaxFrameworkVersion` es un elemento opcional. El `MaxFrameworkVersion` a menos que sea necesario, para no tener que accidentalmente limitar las versiones compatibles de .NET Framework para la plantilla de elemento que se debe omitir. También deben omitirse si .NET Framework no es aplicable a la plantilla.

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

En este ejemplo, la versión máxima de .NET Framework que requiere la plantilla, representado por `MaxFrameworkVersion`, es 4.7.1. Un proyecto creado con esta plantilla puede tener como destino las versiones de .NET Framework hasta 4.7.1.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
