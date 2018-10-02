---
title: Elemento SolutionFolder (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 48a6afddc8f434d03bba75ab55f31666aabdbe39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578495"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [elemento SolutionFolder (plantillas de Visual Studio)](https://docs.microsoft.com/visualstudio/extensibility/solutionfolder-element-visual-studio-templates).  
  
Agrupa los proyectos en plantillas de varios proyectos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
  
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
  
## <a name="remarks"></a>Comentarios  
 Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. El elemento `SolutionFolder` se usa para organizar los proyectos de la plantilla en grupos. Las carpetas especificadas por los elementos `SolutionFolder` se crean como carpetas de soluciones en el proyecto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información sobre las plantillas de varios proyectos, vea [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md).  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md)

