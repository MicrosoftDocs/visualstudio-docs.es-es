---
title: SupportsMasterPage (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
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
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6740145f280e28aca216ee298343bfa661ca5b48
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577862"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [SupportsMasterPage Element (Visual Studio Templates)](https://docs.microsoft.com/visualstudio/extensibility/supportsmasterpage-element-visual-studio-templates).  
  
Especifica si o no la **seleccionar la página maestra** tiene activada la casilla de verificación el **Agregar nuevo elemento** cuadro de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SupportsMasterPage >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica los datos que clasifican la plantilla y define cómo se muestra en el **nuevo proyecto** o **nuevo elemento** cuadro de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser `true` o `false`, lo que indica si el **seleccionar la página maestra** tiene activada la casilla de verificación el **Agregar nuevo elemento** cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
 `SupportsMasterPage` es un elemento opcional. El valor predeterminado es `false`.  
  
 El `SupportsMasterPage` elemento solo está disponible para plantillas de elementos Web.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos de un proyecto Web que incluye compatibilidad para una página maestra.  
  
```  
<VSTemplate Version="3.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
        <Icon>icon.ico</Icon>  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        <DefaultName>WebSite</DefaultName>  
        <SupportsMasterPage>true</SupportsMasterPage>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="WebApplication.webproj">  
            <ProjectItem>icon.ico</ProjectItem>  
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>  
            <ProjectItem>Default.aspx.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)

