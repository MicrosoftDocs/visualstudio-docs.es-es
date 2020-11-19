---
title: SupportsCodeSeparation (Elemento, Plantillas de Visual Studio)
titleSuffix: ''
description: Obtenga información sobre el elemento Supportscodeseparation (y cómo especifica si la casilla colocar el código en un archivo independiente está habilitada en el cuadro de diálogo Agregar nuevo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1847d5f0a0fa77b1dd0ddd0d74eeba84326d0205
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901861"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation (Elemento, Plantillas de Visual Studio)
Especifica si la casilla **colocar el código en un archivo independiente** está habilitada o no en el cuadro de diálogo **Agregar nuevo elemento** .

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Sintaxis

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **nuevo proyecto** o **nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser `true` o `false` , lo que indica si la casilla **colocar el código en un archivo independiente** está habilitada o no en el cuadro de diálogo **Agregar nuevo elemento** .

## <a name="remarks"></a>Observaciones
 `SupportsCodeSeparation` es un elemento opcional. El valor predeterminado es `false`.

 El `SupportsCodeSeparation` elemento solo está disponible para las plantillas de elementos Web.

 La separación de código o el modelo de página de código subyacente le permiten mantener el marcado en un archivo y el código de programación en otro archivo. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y otros lenguajes .NET usan este modelo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se especifica que se muestra la opción **colocar el código en un archivo independiente** .

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Consulte también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
