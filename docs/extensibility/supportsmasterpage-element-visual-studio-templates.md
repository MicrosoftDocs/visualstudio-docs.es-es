---
title: Elemento SupportsMasterPage (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 384672303d00b72431820b98fa02d09e440a1de5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699448"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage (Elemento, Plantillas de Visual Studio)
Especifica si la casilla de verificación **Seleccionar página maestra** está habilitada en el cuadro de diálogo Agregar nuevo **elemento.**

 \<VSTemplate \<> TemplateData> \<SupportsMasterPage>

## <a name="syntax"></a>Sintaxis

```
<SupportsMasterPage> true/false </SupportsMasterPage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica los datos que clasifican la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Nuevo elemento.**|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe `true` `false`ser o , indicando si la casilla **Seleccionar página maestra** está habilitada en el cuadro de diálogo Agregar nuevo **elemento.**

## <a name="remarks"></a>Observaciones
 `SupportsMasterPage` es un elemento opcional. El valor predeterminado es `false`.

 El `SupportsMasterPage` elemento solo está disponible para plantillas de elementos web.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de un proyecto Web que incluye compatibilidad con una página maestra.

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
        <SupportsMasterPage>true</SupportsMasterPage>
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
