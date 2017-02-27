---
title: "CustomDataSignature (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<CustomDataSignature> (Elemento, Plantillas de Visual Studio)"
  - "CustomDataSignature (Elemento, Plantillas de Visual Studio)"
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomDataSignature (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la firma de texto para localizar los datos personalizados.  
  
## Sintaxis  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
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
  
 El texto es una cadena que tiene la firma del texto requerida para localizar los datos personalizados.  
  
## Comentarios  
 `CustomDataSignature` es un elemento opcional.  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)