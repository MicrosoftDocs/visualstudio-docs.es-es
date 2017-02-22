---
title: "Icon (elemento) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, icono"
  - "Icon (elemento) (esquema VSCT XML)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Icon (elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El atributo guid de la etiqueta de icono es el guid de un mapa de bits definido.  El atributo id, selecciona la ranura en la franja de mapa de bits. Este elemento es opcional.  Si este elemento se omite el valor de **guidOfficeIcon:msotcidNoIcon** se que implica.  
  
## Sintaxis  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. El guid de un mapa de bits definido.|  
|id|Obligatorio. Selecciona la ranura en la franja de mapa de bits.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de botones](../extensibility/buttons-element.md)||  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)