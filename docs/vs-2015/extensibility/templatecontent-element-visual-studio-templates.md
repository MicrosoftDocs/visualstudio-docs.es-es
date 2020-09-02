---
title: TemplateContent (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe87bff62c1044442b579664fb789f918a2e6c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186459"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica el contenido de la plantilla.  
  
 \<VSTemplate>  
 \<TemplateContent>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Especifica si se debe compilar la solución cuando se crea un proyecto a partir de la plantilla.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica la organización y el contenido de las plantillas de varios proyectos.|  
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica los archivos o directorios que se van a agregar al proyecto.|  
|[Referencias](../extensibility/references-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica las referencias de ensamblado necesarias para una plantilla de elemento.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Elemento opcional.<br /><br /> Especifica un archivo contenido en la plantilla.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Especifica los parámetros personalizados que se van a usar cuando se crea un proyecto o un elemento a partir de la plantilla.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, la plantilla de elemento o Starter Kit.|  
  
## <a name="remarks"></a>Comentarios  
 `TemplateContent` es un elemento necesario.  
  
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
