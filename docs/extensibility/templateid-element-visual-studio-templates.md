---
title: "TemplateID (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID"
helpviewer_keywords: 
  - "<TemplateID> (elemento) [plantillas de Visual Studio]"
  - "TemplateID (elemento) [plantillas de Visual Studio]"
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# TemplateID (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica un identificador para una plantilla de elementos que se clasifica en un grupo de plantillas de elementos según el elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md).  
  
## Sintaxis  
  
```  
<TemplateID> ... </TemplateID>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
  
## Valor de texto  
 `string` que representa un identificador para una plantilla de elementos que se clasifica en un grupo de plantillas de elementos según el elemento `TemplateGroupID`.  
  
## Comentarios  
 `TemplateID` es un elemento opcional.  
  
 Si un archivo .vstemplate omite el elemento `TemplateID`, se utiliza el elemento [Name](../extensibility/name-element-visual-studio-templates.md) como identificador de la plantilla.  
  
 El valor del elemento `TemplateID` se usa junto con el registro del sistema de proyectos \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Projects\\\) para filtrar las plantillas que aparecen en el cuadro de diálogo **Agregar nuevo elemento**.  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)