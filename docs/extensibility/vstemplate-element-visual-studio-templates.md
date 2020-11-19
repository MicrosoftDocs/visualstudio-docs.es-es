---
title: VSTemplate (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento VSTemplate y cómo contiene todos los metadatos sobre la plantilla de proyecto, la plantilla de elemento o el Starter Kit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973e2ede7e97d1e7710e6571d520be3d8919b9d9
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903486"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate (elemento, plantillas de Visual Studio)
Contiene todos los metadatos sobre la plantilla de proyecto, la plantilla de elemento o el Starter Kit.

## <a name="syntax"></a>Sintaxis

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

| Atributo | Descripción |
|-----------| - |
| `Type` | Identifica la plantilla como una plantilla de proyecto o una plantilla de elemento. Este atributo puede tener un valor de `Project` o `Item` . |
| `Version` | Especifica un número de versión para la plantilla. Las plantillas de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] tienen un `Version` valor de atributo de `3.0.0` . |

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica los datos que categorizan la plantilla y define cómo se muestran en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica el contenido de la plantilla.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Elemento opcional.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Elemento opcional.|

### <a name="parent-elements"></a>Elementos primarios
 Ninguno.

## <a name="remarks"></a>Observaciones
 El `VSTemplate` elemento es el elemento raíz de los archivos *. vstemplate* .

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
