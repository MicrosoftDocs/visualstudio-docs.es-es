---
title: SupportsMasterPage ((elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento SupportsMasterPage (y cómo especifica si está habilitada o no la casilla seleccionar página maestra en el cuadro de diálogo Agregar nuevo elemento.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e9509d7bc0f8141b01ed1a0a600fa5d77a6d6916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839381"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage (Elemento, Plantillas de Visual Studio)
Especifica si está habilitada o no la casilla **seleccionar página maestra** en el cuadro de diálogo **Agregar nuevo elemento** .

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica los datos que categorizan la plantilla y define cómo se muestran en el cuadro de diálogo **nuevo proyecto** o **nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe ser `true` o `false` , lo que indica si la casilla **seleccionar página maestra** está habilitada o no en el cuadro de diálogo **Agregar nuevo elemento** .

## <a name="remarks"></a>Notas
 `SupportsMasterPage` es un elemento opcional. El valor predeterminado es `false`.

 El `SupportsMasterPage` elemento solo está disponible para las plantillas de elementos Web.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de un proyecto web que incluye compatibilidad con una página maestra.

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
- [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
