---
title: "Project (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Project"
helpviewer_keywords: 
  - "<Project> (elemento) [plantillas de Visual Studio]"
  - "Project (elemento) [plantillas de Visual Studio]"
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Project (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica los archivos o directorios que se agregarán al proyecto.  
  
## Sintaxis  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`File`|Atributo necesario.<br /><br /> Especifica el nombre del archivo de proyecto en el archivo .zip de la plantilla.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Valor booleano que especifica si el archivo de proyecto tiene valores de parámetros que se deben reemplazar al crear un proyecto a partir de la plantilla.  El valor predeterminado es `false`.|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica el nombre del archivo de proyecto al crear un proyecto a partir de la plantilla.|  
|`IgnoreProjectParameter`|Atributo opcional.<br /><br /> Especifica si el proyecto se debe agregar a la solución actual.  Si el valor del parámetro personalizado, “$*myCustomParameter*$” existe en el archivo de reemplazo de parámetros, se crea pero no se agrega el proyecto como parte de la solución actualmente abierta.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Carpeta](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica una carpeta que se agregará al proyecto.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica un archivo que se agregará a un proyecto.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necesario.|  
  
## Comentarios  
 `Project` es un elemento secundario opcional de `TemplateContent`.  
  
 El elemento `Project` se utiliza para especificar un proyecto y, por consiguiente, sólo es válido en plantillas de proyecto.  
  
 Los elementos `Project` pueden tener elementos secundarios [Folder](../extensibility/folder-element-visual-studio-project-templates.md) o [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md), pero no una mezcla de elementos secundarios `Folder` y `ProjectItem`.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cambia el nombre del archivo de proyecto automáticamente basándose en el nombre escrito por el usuario en el cuadro de diálogo **Nuevo proyecto**.  Utilice el atributo `TargetFileName` si desea proporcionar un nombre de archivo alternativo para los archivos de proyecto creados con la plantilla.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto de una aplicación de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
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
</VSTemplate>  
```  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [ProjectItem \(Elemento, Plantillas de proyecto de Visual Studio\)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder \(Elemento, Plantillas de proyecto de Visual Studio\)](../extensibility/folder-element-visual-studio-project-templates.md)