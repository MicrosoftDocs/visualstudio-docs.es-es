---
title: ProjectCollection (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9457b1142c94658da489ce7401b7c22d28df903d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193923"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica la organización y el contenido de las plantillas de varios proyectos.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
## <a name="remarks"></a>Comentarios  
 Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. El `ProjectCollection` elemento se usa para especificar los proyectos que se van a incluir en la plantilla. Para obtener más información sobre las plantillas de varios proyectos, vea [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra un archivo .vstemplate raíz simple de varios proyectos. En este ejemplo, la plantilla contiene dos proyectos, `My Windows Application` y `My Class Library`. El atributo `ProjectName` del elemento `ProjectTemplateLink` establece el nombre que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debe asignar a este proyecto. Si el atributo `ProjectName` no existe, se utiliza el nombre del archivo .vstemplate como nombre del proyecto.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)   
 [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md)
