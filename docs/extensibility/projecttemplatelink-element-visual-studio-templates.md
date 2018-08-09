---
title: Elemento ProjectTemplateLink (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c3e539824c815d62d8cf3350b4d823314996677
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636418"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>Elemento ProjectTemplateLink (plantillas de Visual Studio)
Especifica la ruta de acceso a la *.vstemplate* archivo de un proyecto en una plantilla de varios proyectos.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<ProjectTemplateLink >  
O bien  
\<VSTemplate >  
 \<TemplateContent >  
 \<ProjectCollection >  
 \<SolutionFolder >  
 \<ProjectTemplateLink >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`ProjectName`|Atributo opcional.<br /><br /> Especifica el nombre de cada proyecto individual en una plantilla de varios proyectos. El **nuevo proyecto** cuadro de diálogo no puede asignar nombres a proyectos individuales.|  
|`CopyParameters`|Permite que todas las variables de la plantilla de grupo principal se copien en cada una de las plantillas vinculadas.<br /><br /> Los parámetros de las plantillas vinculadas tienen un prefijo `"$ext_*$"`. Por ejemplo, si se encuentra en la plantilla del grupo primario el parámetro `$projectname$` tiene un valor **ExampleProject1**, cuando la plantilla vinculada obtiene su turno para ejecutarse, adquiere un parámetro `$ext_projectname$`, que es una copia de la `$projectname$`parámetro desde la plantilla del grupo primario.<br /><br /> Esto permite que las plantillas vinculadas compartan algunos parámetros comunes, para que estos solo se tengan que crear en la plantilla del grupo primario.<br /><br /> Este atributo es opcional y se establece de forma automática en `false` cuando no se incluye.<br /><br /> Apareció por primera vez en Visual Studio 2013 Update 2. Para hacer referencia a la versión correcta del producto, consulte [hacen referencia a ensamblados ofrecidos en Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Especifica la organización y el contenido de las plantillas de varios proyectos.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Agrupa los proyectos en plantillas de varios proyectos.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Este texto especifica la ruta de acceso a la *.vstemplate* archivo de la plantilla.  
  
## <a name="remarks"></a>Comentarios  
 Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. El `ProjectTemplateLink` elemento se usa para especificar la ubicación de la *.vstemplate* archivo para uno de los proyectos en la plantilla. El *.vstemplate* archivo de una plantilla de varios proyecto contiene un `ProjectTemplateLink` (elemento) para cada proyecto de la plantilla. Para obtener más información sobre las plantillas de varios proyectos, vea [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra una raíz simple de varios proyecto *.vstemplate* archivo. En este ejemplo, la plantilla contiene dos proyectos, `My Windows Application` y `My Class Library`. El atributo `ProjectName` del elemento `ProjectTemplateLink` establece el nombre que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe asignar a este proyecto. Si el `ProjectName` atributo no existe, el nombre de la *.vstemplate* archivo se usa como el nombre del proyecto.  
  
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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)   
 [Cómo: crear plantillas de varios proyectos](../ide/how-to-create-multi-project-templates.md)