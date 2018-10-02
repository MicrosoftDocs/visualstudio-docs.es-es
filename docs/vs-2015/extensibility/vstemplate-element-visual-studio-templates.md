---
title: VSTemplate (elemento) (plantillas de Visual Studio) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dad2fb7a9af5e15d00b05f4a4c6cf99f3929e31e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578168"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [VSTemplate Element (Visual Studio Templates)](https://docs.microsoft.com/visualstudio/extensibility/vstemplate-element-visual-studio-templates).  
  
Contiene todos los metadatos acerca de la plantilla de proyecto, la plantilla de elemento o el starter kit de.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Type`|Identifica la plantilla como una plantilla de proyecto o una plantilla de elemento. Este atributo puede tener un valor de `Project` o `Item`.|  
|`Version`|Especifica un número de versión para la plantilla. Las plantillas en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] y [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] tiene un `Version` valor del atributo `3.0.0`.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica los datos que clasifican la plantilla y define cómo se muestra en el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica el contenido de la plantilla.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Elemento opcional.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Elemento opcional.|  
  
### <a name="parent-elements"></a>Elementos primarios  
 Ninguno.  
  
## <a name="remarks"></a>Comentarios  
 El `VSTemplate` elemento es el elemento raíz de los archivos .vstemplate.  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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

