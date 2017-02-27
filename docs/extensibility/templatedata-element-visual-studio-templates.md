---
title: "TemplateData (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData"
helpviewer_keywords: 
  - "TemplateData (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# TemplateData (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.  
  
## Sintaxis  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Nombre](../extensibility/name-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica el nombre de la plantilla tal como aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
|[Descripción](../extensibility/description-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica la descripción de la plantilla tal como aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
|[Icono](../extensibility/icon-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica la ruta de acceso y el nombre de archivo del archivo de imagen que sirve como icono, que aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**, de la plantilla.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla de proyecto para que aparezca bajo el grupo especificado en el cuadro de diálogo **Nuevo proyecto**.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Clasifica la plantilla de proyecto para que aparezca bajo la subcategoría especificada en el cuadro de diálogo **Nuevo proyecto**.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el Id. de la plantilla.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el Id. de grupo de la plantilla.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica un valor que se utiliza para organizar la plantilla, entre otras plantillas de la misma categoría, tal como aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si se crea una carpeta contenedora en la creación de instancias del proyecto.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el nombre que generará el sistema de proyectos de Visual Studio para el proyecto o elemento cuando se cree.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si el sistema de proyectos de Visual Studio generará el nombre predeterminado para un proyecto o elemento cuando se cree.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si el proyecto se puede crear como un proyecto temporal.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si el botón **Examinar** está disponible en el cuadro de diálogo **Nuevo proyecto**, para que los usuarios puedan modificar con facilidad el directorio predeterminado en el que se guarda un nuevo proyecto.|  
|[Hidden](../extensibility/hidden-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el número de categorías primarias que mostrará la plantilla en el cuadro de diálogo **Nuevo proyecto**.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Elemento opcional.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica si el cuadro de texto **Ubicación** del cuadro de diálogo **Nuevo proyecto** se habilita, deshabilita u oculta para la plantilla de proyecto.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Utilice este elemento si la plantilla solo admite una versión mínima específica y versiones posteriores, si las hay, de .NET Framework.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla admite una página maestra para los proyectos web.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla admite la separación del código, o el modelo de página de código subyacente, para los proyectos web.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla es idéntica para los distintos lenguajes, y si la opción **Lenguaje** está disponible en el cuadro de diálogo **Nuevo proyecto**.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica la plataforma de destino de la plantilla de proyecto.  Este elemento especifica que una plantilla de proyecto se utiliza para crear aplicaciones [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, plantilla de elementos o starter kit.|  
  
## Comentarios  
 `TemplateData` es un elemento necesario.  
  
 Si no incluye un elemento opcional, se utiliza el valor predeterminado para ese elemento.  
  
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