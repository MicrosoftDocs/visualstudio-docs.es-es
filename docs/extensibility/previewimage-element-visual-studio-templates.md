---
title: "PreviewImage (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<PreviewImage> (Elemento, Plantillas de Visual Studio)"
  - "PreviewImage (Elemento, Plantillas de Visual Studio)"
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# PreviewImage (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la imagen de vista previa, como nombre de archivo, para la imagen de este tipo que aparecerá en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.  
  
## Sintaxis  
  
```  
<PreviewImage>"filename"</PreviewImage>  
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
 Se requiere un valor de texto.  
  
 El texto debe ser una cadena que representa un nombre de archivo.  
  
## Comentarios  
 `PreviewImage` es un elemento opcional.  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)