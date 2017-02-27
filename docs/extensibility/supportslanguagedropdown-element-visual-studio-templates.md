---
title: "SupportsLanguageDropDown (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown"
helpviewer_keywords: 
  - "<SupportsLanguageDropDown> (elemento) [plantillas de Visual Studio]"
  - "SupportsLanguageDropDown (elemento) [plantillas de Visual Studio]"
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SupportsLanguageDropDown (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica si la plantilla de elemento Web es idéntica para varios lenguajes y si la opción **Lenguaje** está habilitada en el cuadro de diálogo **Agregar nuevo elemento**.  
  
## Sintaxis  
  
```  
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>  
```  
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser `true` o `false`, que indica si la opción **Lenguaje** está disponible o no en el cuadro de diálogo **Agregar nuevo elemento**.  
  
## Comentarios  
 `SupportsLanguageDropDown` es un elemento opcional.  El valor predeterminado es `false`.  
  
 El elemento `SupportsLanguageDropDown` sólo está disponible para las plantillas de elementos de Web.  
  
 Si el valor de este elemento se establece en `true`, la plantilla de elemento será idéntica para todos los lenguajes de programación y la opción **Lenguaje** estará habilitada en el cuadro de diálogo **Agregar nuevo elemento**.  Esta opción permite elegir el lenguaje de programación del nuevo elemento que desea crear a partir de la plantilla.  
  
## Ejemplo  
 El ejemplo siguiente especifica que la opción de lista desplegable **Lenguaje** debe aparecer en el cuadro de diálogo.  
  
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
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)