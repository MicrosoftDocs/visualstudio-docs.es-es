---
title: TemplateData ((elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b122857a4d916379c070e923ed0753b01287f08b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718856"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData (Elemento, Plantillas de Visual Studio)
Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .

 \<VSTemplate > \<TemplateData >

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

| Elemento | Descripción |
| - | - |
| [Nombre](../extensibility/name-element-visual-studio-templates.md) | Elemento necesario.<br /><br /> Especifica el nombre de la plantilla tal y como aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** . |
| [Descripción](../extensibility/description-element-visual-studio-templates.md) | Elemento necesario.<br /><br /> Especifica la descripción de la plantilla tal como aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** . |
| [Icono](../extensibility/icon-element-visual-studio-templates.md) | Elemento necesario.<br /><br /> Especifica la ruta de acceso y el nombre del archivo de imagen que sirve como icono, que aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** de la plantilla. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Elemento necesario.<br /><br /> Clasifica la plantilla de proyecto para que aparezca bajo el grupo especificado en el cuadro de diálogo **nuevo proyecto** . |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Clasifica la plantilla de proyecto para que aparezca en la subcategoría especificada en el cuadro de diálogo **nuevo proyecto** . |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica el identificador de plantilla. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica el identificador del grupo de plantillas. |
| [Orden](../extensibility/sortorder-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica un valor que se usa para organizar la plantilla, entre otras plantillas de la misma categoría, tal y como aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** . |
| [Createnewfolder (](../extensibility/createnewfolder-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si se crea una carpeta contenedora al crear la instancia del proyecto. |
| [Defaultname (](../extensibility/defaultname-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica el nombre que generará el sistema del proyecto de Visual Studio para el proyecto o elemento cuando se crea. |
| [Providedefaultname (](../extensibility/providedefaultname-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si el sistema del proyecto de Visual Studio generará el nombre predeterminado para un proyecto o elemento cuando se crea. |
| [PromptForSaveOnCreation (](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si el proyecto se puede crear como un proyecto temporal (solo Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si el botón **examinar** está disponible en el cuadro de diálogo **nuevo proyecto** para que los usuarios puedan modificar fácilmente el directorio predeterminado en el que se guarda un nuevo proyecto. |
| [Plusvalía](../extensibility/hidden-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si la plantilla aparece en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** . |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica el número de categorías primarias que mostrarán la plantilla en el cuadro de diálogo **nuevo proyecto** . |
| [Locationfieldmruprefix (](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Elemento opcional. |
| [Locationfield (](../extensibility/locationfield-element-visual-studio-project-templates.md) | Elemento opcional.<br /><br /> Especifica si el cuadro de texto **Ubicación** del cuadro de diálogo **nuevo proyecto** está habilitado, deshabilitado u oculto para la plantilla de proyecto. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Use este elemento si la plantilla solo admite una versión mínima específica y versiones posteriores, si las hay, de la .NET Framework. |
| [SupportsMasterPage (](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si la plantilla admite una página maestra para los proyectos Web. |
| [Supportscodeseparation (](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si la plantilla admite la separación de código o el modelo de página de código subyacente para los proyectos Web. |
| [SupportsLanguageDropDown (](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica si la plantilla es idéntica para varios idiomas y si la opción de **idioma** está disponible en el cuadro de diálogo **nuevo proyecto** . |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica la plataforma a la que está orientada la plantilla del proyecto. Este elemento especifica que se usa una plantilla de proyecto para crear [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones. |

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Archivo](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, la plantilla de elemento o Starter Kit.|

## <a name="remarks"></a>Comentarios
 `TemplateData` es un elemento necesario.

 Si no incluye un elemento opcional, se utiliza el valor predeterminado de ese elemento.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto para una aplicación [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

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
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)