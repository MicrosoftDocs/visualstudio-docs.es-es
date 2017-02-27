---
title: "C&#243;mo: Crear plantillas de varios proyectos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas de varios proyectos"
  - "plantillas de proyecto, crear plantillas de varios proyectos"
  - "plantillas de Visual Studio, crear plantillas de varios proyectos"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Crear plantillas de varios proyectos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos.  Cuando se crea un proyecto basado en una plantilla de varios proyectos desde el cuadro de diálogo **Nuevo proyecto**, todos los proyectos de la plantilla se agregan a la solución.  
  
 Una plantilla de varios proyectos debe incluir los elementos siguientes, comprimidos en un archivo .zip:  
  
-   Un archivo .vstemplate raíz para la plantilla de varios proyectos completa.  Este archivo .vstemplate raíz contiene los metadatos que se muestran en el cuadro de diálogo **Nuevo proyecto** y especifica dónde encontrar los archivos .vstemplate de los proyectos de la plantilla.  Este archivo debe estar en la raíz del archivo .zip.  
  
-   Una o más carpetas que contienen los archivos que son necesarios para una plantilla de proyecto completa.  Esto incluye todos los archivos de código del proyecto, así como un archivo .vstemplate para el proyecto.  
  
 Por ejemplo, un archivo .zip de plantilla de varios proyectos que contenga dos proyectos podría tener los archivos y directorios siguientes:  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 El archivo .vstemplate raíz de una plantilla de varios proyectos se diferencia del de una plantilla de un solo proyecto en lo siguiente:  
  
-   El atributo `Type` del elemento `VSTemplate` contiene el valor `ProjectGroup`.  Por ejemplo:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   El elemento `TemplateContent` contiene un elemento `ProjectCollection` que tiene uno o varios elementos `ProjectTemplateLink` que definen las rutas de acceso a los archivos .vstemplate de los proyectos incluidos.  Por ejemplo:  
  
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
  
 Las plantillas de varios proyectos también se comportan de manera diferente que las normales.  Las plantillas de varios proyectos tienen las siguientes características específicas:  
  
-   No se puede asignar nombres a los proyectos individuales de una plantilla de varios proyectos desde el cuadro de diálogo **Nuevo proyecto**.  En su lugar, utilice el atributo `ProjectName` del elemento `ProjectTemplateLink` para especificar el nombre de cada proyecto.  Para obtener más información, vea el primer ejemplo de la sección siguiente.  
  
-   Las plantillas de varios proyectos pueden contener proyectos escritos en distintos lenguajes, pero la plantilla completa propiamente dicha solo se puede colocar en una categoría mediante el elemento `ProjectType`.  
  
### Para crear una plantilla de varios proyectos  
  
1.  Cree los proyectos que desee incluir en la plantilla de varios proyectos.  
  
2.  Cree archivos .vstemplate para cada proyecto.  Para obtener más información, vea [Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md).  
  
3.  Cree un archivo .vstemplate raíz para contener los metadatos de la plantilla de varios proyectos.  Para obtener más información, vea el primer ejemplo de la sección siguiente.  
  
4.  Seleccione los archivos y las carpetas incluidos en la plantilla, haga clic con el botón secundario del mouse en la selección, haga clic en **Enviar a** y, a continuación, haga clic en **Carpeta comprimida \(en zip\)**.  Los archivos y las carpetas se comprimen en un archivo .zip.  
  
5.  Coloque el archivo de plantilla .zip en el directorio de plantillas de proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  de forma predeterminada, este directorio es \\My Documents\\Visual Studio *Versión*\\Templates\\ProjectTemplates \\.  
  
## Ejemplo  
 En este ejemplo se muestra un archivo .vstemplate raíz básico de varios proyectos.  En este ejemplo, la plantilla contiene dos proyectos, `My Windows Application` y `My Class Library`.  El atributo `ProjectName` del elemento `ProjectTemplateLink` establece el nombre que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debe asignar a este proyecto.  Si el atributo `ProjectName` no existe, se utiliza el nombre del archivo .vstemplate como nombre del proyecto.  
  
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
  
## Ejemplo  
 Este ejemplo utiliza el elemento `SolutionFolder` para dividir los proyectos en dos grupos, `Math Classes` y `Graphics Classes`.  La plantilla contiene cuatro proyectos, dos de los cuales se encuentran en cada carpeta de soluciones.  
  
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
  
## Vea también  
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Cómo: Crear plantillas de proyectos](../ide/how-to-create-project-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder \(Elemento, Plantillas de Visual Studio\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink \(Elemento, Plantillas de Visual Studio\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)