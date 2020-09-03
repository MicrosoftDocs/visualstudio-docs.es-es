---
title: Project (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c9708bb8c35e66199aaf3665883307e48a63c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193968"
---
# <a name="project-element-visual-studio-templates"></a>Project (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica los archivos o directorios que se van a agregar al proyecto.  
  
 \<VSTemplate>  
 \<TemplateContent>  
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
|`File`|Atributo necesario.<br /><br /> Especifica el nombre del archivo de proyecto en el archivo. zip de la plantilla.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Valor booleano que especifica si el archivo de proyecto tiene valores de parámetro que deben reemplazarse cuando se crea un proyecto a partir de la plantilla. El valor predeterminado es `false`.|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica el nombre del archivo de proyecto cuando se crea un proyecto a partir de la plantilla.|  
|`IgnoreProjectParameter`|Atributo opcional.<br /><br /> Especifica si el proyecto se debe agregar a la solución actual. Si el valor del parámetro personalizado "$*myCustomParameter*$" existe en el archivo de reemplazo de parámetros, el proyecto se crea pero no se agrega como parte de la solución actualmente abierta.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Carpeta](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica la carpeta que se va a agregar al proyecto.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica un archivo que se va a agregar a un proyecto.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necesario.|  
  
## <a name="remarks"></a>Comentarios  
 `Project` es un elemento secundario opcional de `TemplateContent`.  
  
 El `Project` elemento se usa para especificar un proyecto y, por lo tanto, solo es válido en las plantillas de proyecto.  
  
 `Project` los elementos pueden tener elementos secundarios de [carpeta](../extensibility/folder-element-visual-studio-project-templates.md) o elementos secundarios [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) , pero no una combinación de los `Folder` `ProjectItem` elementos y secundarios.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cambia automáticamente el nombre del archivo de proyecto en función del nombre escrito por el usuario en el cuadro de diálogo **nuevo proyecto** . Utilice el `TargetFileName` atributo si desea proporcionar un nombre de archivo alternativo para los archivos de proyecto creados con la plantilla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto para una [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplicación.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)   
 [ProjectItem (elemento, plantillas de proyecto de Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder (Elemento, Plantillas de proyecto de Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
