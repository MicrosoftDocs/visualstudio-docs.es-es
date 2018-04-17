---
title: SupportsLanguageDropDown (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b02dcf9b54cfec3dcccca62f9529291e01a912f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown (Elemento, Plantillas de Visual Studio)
Especifica si la plantilla de elemento Web es idéntica para varios idiomas y si la **lenguaje** opción está habilitada en el **Agregar nuevo elemento** cuadro de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SupportsLanguageDropDown >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser `true` o `false`, lo que indica si la **lenguaje** opción está disponible desde el **Agregar nuevo elemento** cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
 `SupportsLanguageDropDown` es un elemento opcional. El valor predeterminado es `false`.  
  
 El `SupportsLanguageDropDown` elemento sólo está disponible para plantillas de elementos Web.  
  
 Si el valor de este elemento se establece en `true`, a continuación, la plantilla de elemento es idéntica para todos los lenguajes de programación y la **lenguaje** opción está habilitada en el **Agregar nuevo elemento** cuadro de diálogo. Esta opción permite elegir el lenguaje de programación del nuevo elemento que desea crear a partir de la plantilla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se especifica para mostrar el **lenguaje** desplegable opción.  
  
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
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>  
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