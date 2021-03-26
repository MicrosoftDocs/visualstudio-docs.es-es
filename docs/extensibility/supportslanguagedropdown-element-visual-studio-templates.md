---
title: SupportsLanguageDropDown (Elemento, Plantillas de Visual Studio)
titleSuffix: ''
description: Obtenga información sobre el elemento SupportsLanguageDropDown (y cómo especifica si la plantilla de elemento Web es idéntica para varios idiomas y si la opción Language está habilitada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 67bf92c8c447faac2969bde3f208823158663712
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056082"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown (Elemento, Plantillas de Visual Studio)

Especifica si la plantilla de elementos Web es idéntica para varios idiomas y si la opción de **idioma** está habilitada en el cuadro de diálogo **Agregar nuevo elemento** .

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Sintaxis

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto

 Se requiere un valor de texto.

 El texto debe ser `true` o `false` , lo que indica si la opción de **idioma** está disponible en el cuadro de diálogo **Agregar nuevo elemento** .

## <a name="remarks"></a>Observaciones

 `SupportsLanguageDropDown` es un elemento opcional. El valor predeterminado es `false`.

 El `SupportsLanguageDropDown` elemento solo está disponible para las plantillas de elementos Web.

 Si el valor de este elemento está establecido en `true` , la plantilla de elemento es idéntica para todos los lenguajes de programación y la opción **Language** está habilitada en el cuadro de diálogo **Agregar nuevo elemento** . Esta opción permite elegir el lenguaje de programación del nuevo elemento que se va a crear a partir de la plantilla.

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se especifica que se muestra la opción de lista desplegable de **idioma** .

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
