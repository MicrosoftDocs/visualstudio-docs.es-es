---
title: MaxFrameworkVersion (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento MaxFrameworkVersion y cómo especifica la versión máxima del .NET Framework que requiere la plantilla.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 09ddccece8261a331277d1c143054305f0d08d7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943210"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion (elemento, plantillas de Visual Studio)

Especifica la versión máxima del .NET Framework que requiere la plantilla. Determina el valor más alto disponible en la lista desplegable **versión de .NET Framework de destino** del cuadro de diálogo **nuevo proyecto** . Para que los usuarios puedan seleccionar una versión de .NET Framework, también debe especificar [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) como la versión mínima .NET Framework para la plantilla.

> [!IMPORTANT]
> A partir de la versión 15,6 de Visual Studio 2017, la lista desplegable **versión de .NET Framework de destino** ya no es un filtro para las plantillas mostradas en la sección **plantillas** del cuadro de diálogo **nuevo proyecto** . En su lugar, el menú desplegable versión de la **plataforma de destino** funciona como un selector de plataforma para la plantilla seleccionada.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el número de versión más alto del .NET Framework permitido por la plantilla.

## <a name="remarks"></a>Notas

`MaxFrameworkVersion` es un elemento opcional. Se `MaxFrameworkVersion` debe omitir el elemento a menos que sea necesario, por lo que no se puede limitar accidentalmente el intervalo admitido de versiones de .NET Framework para la plantilla. También se debe omitir si .NET Framework no es aplicable a la plantilla.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran los metadatos de una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla de clase estándar.

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

En este ejemplo, la versión máxima de la .NET Framework que requiere la plantilla, representada por `MaxFrameworkVersion` , es 4.7.1. Un proyecto creado con esta plantilla puede tener como destino .NET Framework versiones hasta 4.7.1.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
