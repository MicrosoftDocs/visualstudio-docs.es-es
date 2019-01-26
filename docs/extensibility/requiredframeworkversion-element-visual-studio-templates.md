---
title: Elemento RequiredFrameworkVersion (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40eefc62eef318bcd9c52a1cbbb966377b3616f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947002"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion (elemento) (plantillas de Visual Studio)

Especifica la versión mínima de .NET Framework que requiere la plantilla. Hace que el **versión de Target Framework** lista desplegable que se mostrará en el **nuevo proyecto** cuadro de diálogo. El `RequiredFrameworkVersion` elemento determina también el valor más bajo disponible en la lista desplegable.

> [!IMPORTANT]
> A partir de Visual Studio 2017 versión 15.6, la **versión de Target Framework** dropdown ya no es un filtro para las plantillas que se muestran en el **plantillas** sección de la **denuevoproyecto** cuadro de diálogo. En su lugar, la lista desplegable funciona como un selector de marco de trabajo para la plantilla seleccionada.

 \<VSTemplate> \<TemplateData> \<RequiredFrameworkVersion>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestran en el el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser el número de versión mínima de .NET Framework que se requiere para la plantilla.

## <a name="remarks"></a>Comentarios

`RequiredFrameworkVersion` es un elemento opcional. Utilice este elemento solo si la plantilla admite una versión mínima específica (y versiones posteriores, si existe) de .NET Framework. Si especifica la `RequiredFrameworkVersion` elemento y la plantilla no es compatible con una versión mínima específica de .NET Framework, el **versión de Target Framework** lista desplegable que se muestra cuando no se aplica.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra los metadatos de un estándar [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla de clase.

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
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Tener como destino una versión específica de .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
