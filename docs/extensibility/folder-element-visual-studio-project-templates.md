---
title: "Folder (Elemento, Plantillas de proyecto de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Folder"
helpviewer_keywords: 
  - "Folder (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Folder (Elemento, Plantillas de proyecto de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica una carpeta que se agregará al proyecto.  
  
## Sintaxis  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Atributo necesario.<br /><br /> Nombre de la carpeta de proyecto.|  
|`TargetFolderName`|Atributo opcional.<br /><br /> Especifica el nombre de la carpeta al crear un proyecto a partir de la plantilla.  El atributo es útil para usar el reemplazo de parámetros para crear un nombre de carpeta o denominar una carpeta con una cadena internacional que no se pueda utilizar directamente en el archivo .zip.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|`Folder`|Especifica una carpeta que se agregará al proyecto.  Los elementos `Folder` pueden contener elementos secundarios `Folder`.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Especifica un archivo que se agregará al proyecto.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Elemento secundario opcional de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## Comentarios  
 `Folder` es un elemento secundario opcional de `Project`.  
  
 Puede utilizar cualquiera de los métodos siguientes para organizar los elementos de proyecto en carpetas dentro de una plantilla:  
  
-   Incluya las carpetas en el archivo .zip de la plantilla y agréguelas al proyecto en el archivo .vstemplate especificando la ruta de acceso al archivo en los elementos `ProjectItem`, sin ningún elemento `Folder`.  Éste es el método recomendado.  Por ejemplo:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Incluya las carpetas en el archivo .zip de la plantilla y agréguelos al proyecto en el archivo .vstemplate con elementos `Folder`.  Por ejemplo:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   No incluya las carpetas en el archivo .zip de la plantilla, pero agregue las carpetas mediante el atributo `TargetFileName` del elemento `ProjectItem`.  Por ejemplo:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos para una plantilla de proyecto de una aplicación Windows de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [ProjectItem \(Elemento, Plantillas de elementos de Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)