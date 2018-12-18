---
title: Elemento LocationField (plantillas de proyecto de Visual Studio) | Microsoft Docs
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
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d7d1abef8213ea06e04d35c05b38295e0b01bd9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778649"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField (Elemento, Plantillas de proyecto de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica si el **ubicación** cuadro de texto en el **nuevo proyecto** cuadro de diálogo está habilitado, deshabilitado u oculto para la plantilla de proyecto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<LocationField >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo muestra en el **nuevo proyecto**.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Los valores válidos son:  
  
-   `Enabled`, que especifica que el **ubicación** cuadro de la **nuevo proyecto** cuadro de diálogo está habilitado.  
  
-   `Disabled`, que especifica que el **ubicación** cuadro de la **nuevo proyecto** cuadro de diálogo está deshabilitado.  
  
-   `Hidden`, que especifica que el **ubicación** cuadro de la **nuevo proyecto** se oculta el cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
 El valor predeterminado es `Enabled`.  
  
 El **ubicación** cuadro de texto en el **nuevo proyecto** cuadro de diálogo permite a los usuarios cambiar el directorio predeterminado en el que se guardan los nuevos proyectos.  
  
 El valor especificado en el `Location` elemento solo se admite en el cuadro de diálogo si el sistema de proyectos subyacente lo admite.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestran los metadatos de una plantilla de [!INCLUDE[csprcs](../includes/csprcs-md.md)]:  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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

