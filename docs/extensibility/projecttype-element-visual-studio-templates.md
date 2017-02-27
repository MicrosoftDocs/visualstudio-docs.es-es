---
title: "ProjectType (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType"
helpviewer_keywords: 
  - "ProjectType (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# ProjectType (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Categoriza la plantilla de proyecto para que aparezca bajo el grupo especificado en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.  
  
> [!WARNING]
>  Las plantillas de proyecto se admiten para C\+\+ a partir de Visual Studio 2012.  No se admiten para C\+\+ en Visual Studio 2010 y versiones anteriores.  
  
## Sintaxis  
  
```  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 Este valor especifica el tipo de proyecto que creará la plantilla, y debe contener uno de los valores siguientes:  
  
-   `CSharp`: especifica que la plantilla cree un proyecto o elemento de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
-   `VisualBasic`: especifica que la plantilla cree un proyecto o elemento de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
-   `Web`: especifica que la plantilla cree un proyecto o elemento Web.  Si el elemento `ProjectType` contiene este valor, el lenguaje del proyecto o elemento se define en [ProjectSubType \(Elemento, Plantillas de Visual Studio\)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## Comentarios  
 `ProjectType` es un elemento secundario necesario de `TemplateData`.  
  
 El valor del elemento `ProjectType` especifica dónde se encuentra la plantilla en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.  Por ejemplo, una plantilla con un valor `ProjectType` de `CSharp` aparece bajo el nodo **Visual C\#** en el cuadro de diálogo **Nuevo proyecto**.  
  
 Un subtipo de plantilla se puede especificar utilizando el elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
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
 [ProjectSubType \(Elemento, Plantillas de Visual Studio\)](../extensibility/projectsubtype-element-visual-studio-templates.md)