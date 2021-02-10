---
title: FullClassName (elemento, extensión del Asistente para plantillas de VS)
description: Obtenga información sobre el elemento FullClassName y cómo es el nombre completo de la clase que implementa la interfaz IWizard.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d23bb194dfadd202cf2899b1834f3b6ceeaa2b3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968208"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>FullClassName (elemento, extensión del Asistente para plantillas de Visual Studio)
Nombre completo de la clase que implementa la `IWizard` interfaz.

 \<VSTemplate> \<WizardExtension>
... \<FullClassName>

## <a name="syntax"></a>Sintaxis

```xml
<FullClassName>ClassName</FullClassName>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene los elementos de registro para personalizar el Asistente para plantillas.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Este texto especifica la clase que implementa la `IWizard` interfaz. La clase especificada debe existir en el ensamblado especificado por el elemento [Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) .

## <a name="remarks"></a>Notas
 `FullClassName` es un elemento secundario obligatorio de `WizardExtension`.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de la plantilla de proyecto estándar para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación Windows.

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
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Cómo: usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md)
