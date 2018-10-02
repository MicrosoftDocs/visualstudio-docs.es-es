---
title: Proyecto de elemento (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5c318d26c0a09aaca03cb0043c2b0eb54d43146
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579107"
---
# <a name="project-element-visual-studio-templates"></a>Project (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Project Element (Visual Studio Templates)](https://docs.microsoft.com/visualstudio/extensibility/project-element-visual-studio-templates).  
  
Especifica los archivos o directorios que se agregarán al proyecto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`File`|Atributo necesario.<br /><br /> Especifica el nombre del archivo del proyecto en el archivo .zip de plantilla.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Un valor booleano que especifica si el archivo de proyecto tiene valores de parámetro que se deben reemplazar cuando se crea un proyecto de la plantilla. El valor predeterminado es `false`.|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica el nombre del archivo del proyecto cuando se crea un proyecto de la plantilla.|  
|`IgnoreProjectParameter`|Atributo opcional.<br /><br /> Especifica si el proyecto debe agregarse a la solución actual. Si el valor de parámetro personalizado, "$*myCustomParameter*$" existe en el archivo de reemplazo de parámetro, el proyecto se crea pero no se agrega como parte de la solución actualmente abierta.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Carpeta](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica una carpeta para agregarla al proyecto.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica un archivo para agregar a un proyecto.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necesario.|  
  
## <a name="remarks"></a>Comentarios  
 `Project` es un elemento secundario opcional de `TemplateContent`.  
  
 El `Project` es elemento utilizado para especificar un proyecto y, por lo tanto, sólo es válido en plantillas de proyecto.  
  
 `Project` los elementos pueden tener [carpeta](../extensibility/folder-element-visual-studio-project-templates.md) elementos secundarios o [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) elementos secundarios, pero no una combinación de ambos `Folder` y `ProjectItem` los elementos secundarios.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia el nombre automáticamente el nombre de archivo de proyecto basado en el nombre especificado por el usuario en el **nuevo proyecto** cuadro de diálogo. Use el `TargetFileName` atributo si desea proporcionar un nombre de archivo alternativo para los archivos de proyecto creados con la plantilla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos para una plantilla de proyecto para un [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplicación.  
  
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
 [ProjectItem (elemento) (plantillas de proyecto de Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder (Elemento, Plantillas de proyecto de Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)

