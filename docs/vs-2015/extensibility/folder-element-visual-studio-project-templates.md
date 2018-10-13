---
title: Elemento Folder (plantillas de proyecto de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 486448ec92ef05890c95ec5277e5b5b99e976231
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236163"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder (Elemento, Plantillas de proyecto de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica una carpeta que se agregará al proyecto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<Carpeta >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Atributo necesario.<br /><br /> El nombre de la carpeta del proyecto.|  
|`TargetFolderName`|Atributo opcional.<br /><br /> Especifica el nombre de la carpeta cuando se crea un proyecto de la plantilla. Este atributo es útil para el uso de reemplazo de parámetros para crear un nombre de carpeta o una carpeta con una cadena internacional de nomenclatura no se puede usar directamente en el archivo zip.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|`Folder`|Especifica una carpeta para agregarla al proyecto. `Folder` los elementos pueden contener secundarios `Folder` elementos.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Especifica un archivo para agregar al proyecto.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Elemento secundario opcional de [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|  
  
## <a name="remarks"></a>Comentarios  
 `Folder` es un elemento secundario opcional de `Project`.  
  
 Puede usar cualquiera de los siguientes métodos para organizar los elementos de proyecto en carpetas en una plantilla:  
  
-   Incluir las carpetas en el archivo .zip de plantilla y agregarlos al proyecto en el archivo .vstemplate especificando la ruta de acceso al archivo en el `ProjectItem` elementos, sin ningún `Folder` elementos. Este es el método recomendado. Por ejemplo:  
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   Incluir las carpetas en el archivo .zip de plantilla y agregarlos al proyecto en el archivo .vstemplate con `Folder` elementos. Por ejemplo:  
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   No incluya carpetas en el archivo .zip de plantilla, pero agregue carpetas mediante la `TargetFileName` atributo de la `ProjectItem` elemento. Por ejemplo:  
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos de una plantilla de proyecto para un [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplicación de Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [ProjectItem (Elemento, Plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)

