---
title: Elemento SupportsCodeSeparation (Plantillas de Visual Studio) Microsoft Docs
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
ms.openlocfilehash: bd52ae47f47f3ca1fce23f7cf8d37260ec86fb0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699507"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation (Elemento, Plantillas de Visual Studio)
Especifica si la casilla **Colocar código en un archivo independiente** está habilitada en el cuadro de diálogo Agregar nuevo **elemento.**

 \<VSTemplate \<> TemplateData> \<SupportsCodeSeparation>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Nuevo elemento.**|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe `true` `false`ser o , indicando si la casilla de verificación **Colocar código en archivo independiente** está habilitada en el cuadro de diálogo Agregar nuevo **elemento.**

## <a name="remarks"></a>Observaciones
 `SupportsCodeSeparation` es un elemento opcional. El valor predeterminado es `false`.

 El `SupportsCodeSeparation` elemento solo está disponible para plantillas de elementos web.

 La separación de código, o el modelo de página de código subyacente, le permite mantener el marcado en un archivo y el código de programación en otro archivo. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]y otros lenguajes .NET usan este modelo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se especifica que se muestre la opción **Colocar código en un archivo independiente.**

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

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
