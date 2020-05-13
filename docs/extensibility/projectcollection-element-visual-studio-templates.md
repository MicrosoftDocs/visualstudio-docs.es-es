---
title: Elemento ProjectCollection (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701971"
---
# <a name="projectcollection-element-visual-studio-templates"></a>Elemento ProjectCollection (plantillas de Visual Studio)
Especifica la organización y el contenido de las plantillas de varios proyectos.

 \<VSTemplate \<> TemplateContent> \<> ProjectCollection

## <a name="syntax"></a>Sintaxis

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica un proyecto en una plantilla de varios proyectos.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Agrupa los proyectos en plantillas de varios proyectos.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica el contenido de la plantilla.|

## <a name="remarks"></a>Observaciones
 Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. El `ProjectCollection` elemento se utiliza para especificar los proyectos que se contienen en la plantilla. Para obtener más información sobre las plantillas de varios proyectos, consulte [Cómo: Crear plantillas de varios proyectos.](../ide/how-to-create-multi-project-templates.md)

## <a name="example"></a>Ejemplo
 En este ejemplo se muestra un archivo *.vstemplate* raíz de varios proyectos simple. En este ejemplo, la plantilla contiene dos proyectos, `My Windows Application` y `My Class Library`. El atributo `ProjectName` del elemento `ProjectTemplateLink` establece el nombre que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe asignar a este proyecto. Si `ProjectName` el atributo no existe, el nombre del archivo *.vstemplate* se utiliza como nombre del proyecto.

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
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Cómo: Crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md)
