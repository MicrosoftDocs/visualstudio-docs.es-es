---
title: EnableLocationBrowseButton (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef9f42bfb24caaf2775ba2c70110eaaa5d616116
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204595"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica si el **examinar** botón está disponible en el **nuevo proyecto** cuadro de diálogo para que los usuarios puedan modificar fácilmente el directorio predeterminado donde se guarda un nuevo proyecto.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<EnableLocationBrowseButton>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser `true` o `false`, que indica si se deben mostrar el **examinar** situado en la **nuevo proyecto** cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
 `EnableLocationBrowseButton` es un elemento opcional. El valor predeterminado es `true`, que muestra la **examinar** situado en la **nuevo proyecto** cuadro de diálogo.  
  
 En el **nuevo proyecto** cuadro de diálogo, el **ubicación** cuadro de texto especifica el directorio donde se guarda un nuevo proyecto. El **examinar** botón le ayuda a modificar este directorio mostrando el **ubicación del proyecto** cuadro de diálogo que le permite desplazarse fácilmente a un directorio diferente que está disponible en el equipo, y a continuación, elija como el directorio donde se guarda el nuevo proyecto.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos de un [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplicación de Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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
