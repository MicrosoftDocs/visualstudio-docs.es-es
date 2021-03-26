---
title: SolutionFolder (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento SolutionFolder y cómo agrupa los proyectos en plantillas de varios proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f65607a5411270e7f21e6ec6cdac0c087824b32b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056342"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder (Elemento, Plantillas de Visual Studio)
Agrupa los proyectos en plantillas de varios proyectos.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>

## <a name="syntax"></a>Sintaxis

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Atributo necesario.<br /><br /> Nombre de la carpeta de soluciones.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica la ruta de acceso al archivo .vstemplate de un proyecto en una plantilla de varios proyectos.|
|`SolutionFolder`|Elemento opcional.<br /><br /> Agrupa los proyectos en plantillas de varios proyectos.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Especifica la organización y el contenido de las plantillas de varios proyectos.|
|`SolutionFolder`|Agrupa los proyectos en plantillas de varios proyectos.|

## <a name="remarks"></a>Observaciones
 Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. El elemento `SolutionFolder` se usa para organizar los proyectos de la plantilla en grupos. Las carpetas especificadas por los elementos `SolutionFolder` se crean como carpetas de soluciones en el proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información sobre las plantillas de varios proyectos, vea [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Ejemplo
 Este ejemplo usa el elemento `SolutionFolder` para dividir la plantilla de varios proyectos en dos grupos, `Math Classes` y `Graphics Classes`. La plantilla contiene cuatro proyectos, dos de los cuales se colocan en cada carpeta de soluciones.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Consulte también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
- [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md)
