---
title: Elemento RequiredFrameworkVersion (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701512"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>Elemento RequiredFrameworkVersion (plantillas de Visual Studio)

Especifica la versión mínima de .NET Framework que requiere la plantilla. Hace que el menú desplegable **Versión** de marco de trabajo de destino se muestre en el cuadro de diálogo **Nuevo proyecto.** El `RequiredFrameworkVersion` elemento también determina el valor más bajo disponible en la lista desplegable.

> [!IMPORTANT]
> A partir de Visual Studio 2017 versión 15.6, la lista desplegable **Versión** de marco de trabajo de destino ya no es un filtro para las plantillas mostradas en la sección **Plantillas** del cuadro de diálogo **Nuevo proyecto.** En su lugar, la lista desplegable funciona como un selector de marco de trabajo para la plantilla seleccionada.

 \<VSTemplate \<> TemplateData> \<>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o Agregar **nuevo elemento.**|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el número de versión mínimo de .NET Framework que se requiere para la plantilla.

## <a name="remarks"></a>Observaciones

`RequiredFrameworkVersion` es un elemento opcional. Use este elemento solo si la plantilla admite una versión mínima específica (y versiones posteriores, si las hay) de .NET Framework. Si especifica `RequiredFrameworkVersion` el elemento y la plantilla no admite una versión mínima específica de .NET Framework, la lista desplegable **Versión** de marco de destino se muestra cuando no es aplicable.

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

En este ejemplo, la versión mínima de .NET Framework que `RequiredFrameworkVersion`requiere la plantilla, representada por , es 3.0. Un proyecto creado con esta plantilla puede tener como destino versiones de .NET Framework a partir de 3.0.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md)
