---
title: "ProjectSubType (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType"
helpviewer_keywords: 
  - "<ProjectSubType> (elemento) [plantillas de Visual Studio]"
  - "ProjectSubType (elemento) [plantillas de Visual Studio]"
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectSubType (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Clasifica la plantilla en una subcategoría del valor especificado en el elemento `ProjectType`.  
  
## Sintaxis  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
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
  
 Este valor especifica la subcategoría de la plantilla.  
  
## Comentarios  
 `ProjectSubType` es un elemento secundario opcional de `TemplateData`.  
  
 El elemento `ProjectSubType` proporciona una subcategoría del elemento [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md).  Este valor puede incluir:  
  
-   `SmartDevice-NETCFv1`: especifica que la plantilla está destinada a la versión 1.0 de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
-   `SmartDevice-NETCFv2`: especifica que la plantilla está destinada a la versión 2.0 de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
 Si una plantilla contiene un elemento `ProjectType` con un valor de `Web`, el elemento `ProjectSubType` especifica el lenguaje de programación de la plantilla.  Este elemento puede tener los valores siguientes:  
  
-   `CSharp`: especifica que la plantilla cree un proyecto o elemento web de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
-   `VisualBasic`: especifica que la plantilla cree un proyecto o elemento web de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto de una aplicación para dispositivos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] destinada a la versión 2.0 de [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
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
 [ProjectType \(Elemento, Plantillas de Visual Studio\)](../extensibility/projecttype-element-visual-studio-templates.md)