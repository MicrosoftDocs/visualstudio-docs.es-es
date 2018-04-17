---
title: TemplateData (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbf5b4c26b46c0be6038651a41c751afc39e4da5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData (Elemento, Plantillas de Visual Studio)
Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .  
  
 \<VSTemplate >  
 \<TemplateData >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Name](../extensibility/name-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica el nombre de la plantilla, tal y como aparece en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
|[Descripción](../extensibility/description-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica la descripción de la plantilla, tal y como aparece en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
|[Iconos](../extensibility/icon-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica la ruta de acceso y el nombre de archivo del archivo de imagen que sirve como icono, que aparece en la vista de la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo, para la plantilla.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla de proyecto para que aparezca bajo el grupo especificado en el **nuevo proyecto** cuadro de diálogo.|  
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Clasifica la plantilla de proyecto para que aparezca bajo la subcategoría especificada en el **nuevo proyecto** cuadro de diálogo.|  
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el identificador de plantilla.|  
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el identificador de grupo de plantilla.|  
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica un valor que se utiliza para organizar la plantilla, entre otras plantillas de la misma categoría, tal y como aparece en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si se crea una carpeta contenedora en la creación de instancias del proyecto.|  
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el nombre que el sistema de proyectos de Visual Studio generará para el proyecto o elemento cuando se crea.|  
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si el sistema de proyectos de Visual Studio generará el nombre predeterminado para un proyecto o elemento cuando se crea.|  
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si se puede crear el proyecto como un proyecto temporal.|  
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si el **examinar** botón está disponible en la **nuevo proyecto** cuadro de diálogo para que los usuarios pueden modificar fácilmente el directorio predeterminado donde se guarda un nuevo proyecto.|  
|[Oculto](../extensibility/hidden-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla aparece en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica el número de categorías primarias que mostrará la plantilla en el **nuevo proyecto** cuadro de diálogo.|  
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Elemento opcional.|  
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica si el **ubicación** cuadro de texto en el **nuevo proyecto** cuadro de diálogo está habilitado, deshabilitado o en la plantilla de proyecto ocultos.|  
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Utilice este elemento si la plantilla solo es compatible con una versión mínima específica y versiones posteriores, si la hubiera, de .NET Framework.|  
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla admite una página maestra para proyectos web.|  
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla admite la separación de código o el modelo de página de código subyacente, para los proyectos web.|  
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica si la plantilla es idéntica para varios idiomas y si la **lenguaje** opción está disponible desde el **nuevo proyecto** cuadro de diálogo.|  
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica la plataforma a la que está orientada la plantilla del proyecto. Este elemento especifica que se usa una plantilla de proyecto para crear [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, una plantilla de elemento o un kit de inicio.|  
  
## <a name="remarks"></a>Comentarios  
 `TemplateData` es un elemento necesario.  
  
 Si no incluye un elemento opcional, se usa el valor predeterminado para ese elemento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra los metadatos de una plantilla de proyecto para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)