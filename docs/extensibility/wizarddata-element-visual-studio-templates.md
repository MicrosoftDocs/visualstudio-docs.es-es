---
title: Elemento WizardData (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3f9d2e971d944b964f4b194d1324ff960fbd24
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740391"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData (Elemento, Plantillas de Visual Studio)

Especifica XML personalizado

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Sintaxis

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, la plantilla de elemento o el kit de inicio.|

## <a name="text-value"></a>Valor de texto

El valor de texto es opcional.

Este texto especifica el XML personalizado que se va a pasar a la extensión del asistente personalizado especificada en el [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) elemento.

## <a name="remarks"></a>Observaciones

Cualquier XML se puede especificar en este elemento. El XML se pasará como parámetro a la extensión del asistente personalizado, lo que permite que la extensión use el contenido de este elemento. No se realiza ninguna validación en estos datos.

El contenido del elemento **WizardData** se pasa, sin cambios, como `IWizard.RunStarted` un parámetro dentro del diccionario de cadenas de parámetros en el método. La clave del `$wizarddata$`diccionario se denomina .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran los metadatos de la plantilla de proyecto estándar para una aplicación de Windows de C.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
- [WizardExtension (Elemento, Plantillas de Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Cómo: Utilizar los asistentes con las plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)
