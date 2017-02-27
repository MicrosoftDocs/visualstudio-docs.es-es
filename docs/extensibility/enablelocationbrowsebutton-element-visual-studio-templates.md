---
title: "EnableLocationBrowseButton (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton"
helpviewer_keywords: 
  - "EnableLocationBrowseButton [plantillas de proyecto de Visual Studio]"
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EnableLocationBrowseButton (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica si el botón **Examinar** está disponible en el cuadro de diálogo **Nuevo proyecto**, para que los usuarios puedan modificar con facilidad el directorio predeterminado en el que se guarda un nuevo proyecto.  
  
## Sintaxis  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser `true` o `false`, indicando si hay que mostrar o no el botón **Examinar** en el cuadro de diálogo **Nuevo proyecto**.  
  
## Comentarios  
 `EnableLocationBrowseButton` es un elemento opcional.  El valor predeterminado es `true`, lo que muestra el botón **Examinar** en el cuadro de diálogo **Nuevo proyecto**.  
  
 En el cuadro de diálogo **Nuevo proyecto**, el cuadro de texto **Ubicación** especifica el directorio donde se guarda un nuevo proyecto.  El botón **Examinar** ayuda a modificar este directorio mostrando el cuadro de diálogo **Ubicación del proyecto**, que permite navegar con facilidad a un directorio diferente que esté disponible en el equipo y, a continuación, elegirlo como el directorio en el que se guarda el nuevo proyecto.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una aplicación Windows de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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