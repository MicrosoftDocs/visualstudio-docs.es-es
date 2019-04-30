---
title: WizardExtension (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5e398125f467f4e5211573e96cd53bc0bc8d6dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553768"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension (Elemento, Plantillas de Visual Studio)
Contiene los elementos de registro para personalizar al Asistente para la plantilla.

 \<VSTemplate >... \<WizardExtension>

## <a name="syntax"></a>Sintaxis

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Ensamblado](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|Elemento necesario.<br /><br /> Especifica el nombre o el nombre seguro de un ensamblado que aparece en la caché global de ensamblados. Debe haber al menos una `Assembly` elemento en un `WizardExtension` elemento.|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|Elemento necesario.<br /><br /> El nombre completo de la clase que implementa el `IWizard` interfaz. Debe haber al menos una `FullClassName` elemento en un `WizardExtension` elemento.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Contiene todos los metadatos de la plantilla de proyecto, la plantilla de elemento o el starter kit de.|

## <a name="remarks"></a>Comentarios
 `WizardExtension` es un elemento secundario opcional de `VSTemplate`.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los metadatos de la plantilla de proyecto estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación de Windows.

```
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
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)
- [Cómo: Usar asistentes con plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)