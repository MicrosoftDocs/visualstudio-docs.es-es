---
title: "LocationField (Elemento, Plantillas de proyecto de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#LocationField"
helpviewer_keywords: 
  - "LocationField (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# LocationField (Elemento, Plantillas de proyecto de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica si el **ubicación** cuadro de texto en el **nuevo proyecto** cuadro de diálogo está habilitado, deshabilitado u oculto para la plantilla de proyecto.  
  
 \<VSTemplate\>  
 \<TemplateData\>  
 \<LocationField\>  
  
## Sintaxis  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el **nuevo proyecto**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 Los valores válidos son:  
  
-   `Enabled`, que especifica que el **ubicación** cuadro de la **nuevo proyecto** cuadro de diálogo está habilitado.  
  
-   `Disabled`, que especifica que el **ubicación** cuadro de la **nuevo proyecto** cuadro de diálogo está deshabilitado.  
  
-   `Hidden`, que especifica que el **ubicación** cuadro de la **nuevo proyecto** se oculta el cuadro de diálogo.  
  
## Comentarios  
 El valor predeterminado es `Enabled`.  
  
 El **ubicación** cuadro de texto en el **nuevo proyecto** cuadro de diálogo permite a los usuarios cambiar el directorio predeterminado donde se guardan los nuevos proyectos.  
  
 El valor especificado en el `Location` elemento solo se admite en el cuadro de diálogo si el sistema de proyectos subyacente lo admite.  
  
## Ejemplo  
 En el siguiente ejemplo se muestran los metadatos de una plantilla de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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