---
title: Elemento FullClassName (extensión del asistente de plantilla VS)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e533fdf5b5497b17949581801721136b18bc2d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711430"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Elemento FullClassName (extensión del asistente de plantillas de Visual Studio)
El nombre completo de la clase `IWizard` que implementa la interfaz.

 \<VSTemplate \<> WizardExtension> ... \<FullClassName>

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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene los elementos de registro para personalizar el asistente de plantilla.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Este texto especifica la clase `IWizard` que implementa la interfaz. La clase especificada debe existir en el ensamblado especificado por el [Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) elemento.

## <a name="remarks"></a>Observaciones
 `FullClassName` es un elemento secundario obligatorio de `WizardExtension`.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadatos de la plantilla de proyecto estándar para una aplicación de Windows.

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
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Cómo: Usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md)
