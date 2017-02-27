---
title: "WizardData (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#WizardData"
helpviewer_keywords: 
  - "<WizardData> (elemento) [plantillas de Visual Studio]"
  - "WizardData (elemento) [plantillas de Visual Studio]"
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# WizardData (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica código XML personalizado  
  
## Sintaxis  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, plantilla de elementos o starter kit.|  
  
## Valor de texto  
 El valor de texto es opcional.  
  
 Este texto especifica el código XML personalizado que se va a pasar a la extensión de asistente personalizada especificada en el elemento [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
## Comentarios  
 Se puede especificar cualquier código XML en este elemento.  El código XML se pasará como un parámetro a la extensión de asistente personalizada, permitiendo a la extensión utilizar el contenido de este elemento.  No se realiza ninguna validación en estos datos.  
  
 El contenido del elemento`WizardData` se pasa, sin modificar, como un parámetro dentro del diccionario de cadenas de parámetros en el método `IWizard.RunStarted`.  El parámetro se denomina $WizardData$.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto estándar de una aplicación Windows de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [WizardExtension \(Elemento, Plantillas de Visual Studio\)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Cómo: Utilizar los asistentes con las plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)