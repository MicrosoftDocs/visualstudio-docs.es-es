---
title: "SupportsMasterPage (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage"
helpviewer_keywords: 
  - "<SupportsMasterPage> (elemento) [plantillas de Visual Studio]"
  - "SupportsMasterPage (elemento) [plantillas de Visual Studio]"
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SupportsMasterPage (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica si se habilita o no la casilla **Seleccionar la página maestra** en el cuadro de diálogo **Agregar nuevo elemento**.  
  
## Sintaxis  
  
```  
<SupportsMasterPage> true/false </SupportsMasterPage>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica datos que categorizan la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Nuevo elemento**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser `true` o `false`, indicando si se activa o no la casilla **Seleccionar la página maestra** en el cuadro de diálogo **Agregar nuevo elemento**.  
  
## Comentarios  
 `SupportsMasterPage` es un elemento opcional.  El valor predeterminado es `false`.  
  
 El elemento `SupportsMasterPage` sólo está disponible para las plantillas de elementos Web.  
  
## Ejemplo  
 El ejemplo siguiente muestra los metadatos de un proyecto web que incluye compatibilidad para una página maestra.  
  
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
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)