---
title: 'Cómo: Crear plantillas de varios proyectos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce7147df5b15dd6aaa639c27b2d2ffbc0b3d3152
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567368"
---
# <a name="how-to-create-multi-project-templates"></a>Cómo: Crear plantillas de varios proyectos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: crear plantillas de varios proyectos](https://docs.microsoft.com/visualstudio/ide/how-to-create-multi-project-templates).  
  
Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. Cuando se crea un proyecto basado en una plantilla de varios proyectos a partir del cuadro de diálogo **Nuevo proyecto**, todos los proyectos de la plantilla se agregan a la solución.  
  
 Una plantilla de varios proyectos debe incluir los elementos siguientes, comprimidos en un archivo .zip:  
  
-   Un archivo raíz .vstemplate para toda la plantilla de varios proyectos. Este archivo raíz .vstemplate contiene los metadatos que muestra el cuadro de diálogo **Nuevo proyecto** y especifica dónde encontrar los archivos .vstemplate para los proyectos de esta plantilla. Este archivo debe estar ubicado en la raíz del archivo .zip.  
  
-   Una o varias carpetas que contienen los archivos que son necesarios para una plantilla de proyecto completa. Esto incluye todos los archivos de código del proyecto, así como un archivo .vstemplate para el proyecto.  
  
 Por ejemplo, un archivo .zip de plantilla de varios proyectos que tiene dos proyectos podría tener los siguientes archivos y directorios:  
  
 MultiProjectTemplate.vstemplate  
  
 \Project1\Project1.vstemplate  
  
 \Project1\Project1.vbproj  
  
 \Project1\Class.vb  
  
 \Project2\Project2.vstemplate  
  
 \Project2\Project2.vbproj  
  
 \Project2\Class.vb  
  
 El archivo raíz .vstemplate de una plantilla de varios proyectos difiere de una plantilla de proyecto único de las siguientes formas:  
  
-   El atributo `Type` del elemento `VSTemplate` contiene el valor `ProjectGroup`. Por ejemplo:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   El elemento `TemplateContent` contiene un elemento `ProjectCollection` que tiene uno o varios elementos `ProjectTemplateLink` que definen las rutas de acceso a los archivos .vstemplate de los proyectos incluidos. Por ejemplo:  
  
    ```  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink>  
                Project1\Project1.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink>  
                Project2\Project2.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
    ```  
  
 Las plantillas de varios proyectos también se comportan de forma diferente a las plantillas normales. Las plantillas de varios proyectos tienen las siguientes características únicas:  
  
-   A los proyectos individuales de una plantilla de varios proyectos no se les puede asignar nombres mediante el cuadro de diálogo **Nuevo proyecto**. En su lugar, use el atributo `ProjectName` en el elemento `ProjectTemplateLink` para especificar el nombre de cada proyecto. Para más información, vea el primer ejemplo de la sección siguiente.  
  
-   Las plantillas de varios proyectos pueden contener proyectos escritos en lenguajes diferentes, pero la plantilla completa solo se puede colocar en una categoría mediante el elemento `ProjectType`.  
  
### <a name="to-create-a-multi-project-template"></a>Para crear una plantilla de varios proyectos  
  
1.  Cree los proyectos que se incluirán en la plantilla de varios proyectos.  
  
2.  Cree los archivos .vstemplate de cada proyecto. Para más información, vea [Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md).  
  
3.  Cree un archivo raíz .vstemplate que contenga los metadatos de la plantilla de varios proyectos. Para más información, vea el primer ejemplo de la sección siguiente.  
  
4.  Seleccione los archivos y las carpetas que se incluirán en la plantilla, haga clic con el botón derecho en la selección, haga clic en **Enviar a** y, después, en **Carpeta comprimida (en zip)**. Los archivos y las carpetas se comprimen en un archivo .zip.  
  
5.  Coloque el archivo de plantilla .zip en el directorio de plantillas de proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. De forma predeterminada, este directorio es \Mis documentos\Visual Studio *Versión*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se muestra un archivo raíz .vstemplate básico de varios proyectos. En este ejemplo, la plantilla contiene dos proyectos, `My Windows Application` y `My Class Library`. El atributo `ProjectName` del elemento `ProjectTemplateLink` establece el nombre que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debe asignar a este proyecto. Si el atributo `ProjectName` no existe, se utiliza el nombre del archivo .vstemplate como nombre del proyecto.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se usa el elemento `SolutionFolder` para dividir los proyectos en dos grupos, `Math Classes` y `Graphics Classes`. La plantilla contiene cuatro proyectos, dos de los cuales se colocan en cada carpeta de soluciones.  
  
```  
<VSTemplate Version="2.0.0" Type="ProjectGroup"  
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
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder Element (Visual Studio Templates)](../extensibility/solutionfolder-element-visual-studio-templates.md)  [Elemento SolutionFolder (Plantillas de Visual Studio)]  
 [ProjectTemplateLink (Elemento, Plantillas de Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)



