---
title: RequiredFrameworkVersion (Elemento, Plantillas de Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 211393ea65f7ca31f80134c48863b0092478b3f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836987"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion (elemento, plantillas de Visual Studio)

Especifica la versión mínima del .NET Framework que requiere la plantilla. Hace que la lista desplegable versión de la **plataforma de destino** se muestre en el cuadro de diálogo **nuevo proyecto** . El `RequiredFrameworkVersion` elemento también determina el valor más bajo disponible en la lista desplegable.

> [!IMPORTANT]
> A partir de la versión 15,6 de Visual Studio 2017, la lista desplegable **versión de .NET Framework de destino** ya no es un filtro para las plantillas mostradas en la sección **plantillas** del cuadro de diálogo **nuevo proyecto** . En su lugar, la lista desplegable funciona como un selector de plataforma para la plantilla seleccionada.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el número de versión mínimo de la .NET Framework que se requiere para la plantilla.

## <a name="remarks"></a>Notas

`RequiredFrameworkVersion` es un elemento opcional. Use este elemento solo si la plantilla admite una versión mínima específica (y versiones posteriores, si hay alguna) de la .NET Framework. Si especifica el `RequiredFrameworkVersion` elemento y la plantilla no es compatible con una versión mínima específica del .NET Framework, la lista desplegable versión de la **plataforma de destino** se muestra cuando no es aplicable.

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

En este ejemplo, la versión mínima de la .NET Framework requerida por la plantilla, representada por `RequiredFrameworkVersion` , es 3,0. Un proyecto creado con esta plantilla puede tener como destino .NET Framework versiones a partir de 3,0.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md)
