---
title: "Formato de un servicio de lenguaje heredado autom&#225;tico | Microsoft Docs"
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
  - "formato de los servicios de lenguaje, automático"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Formato de un servicio de lenguaje heredado autom&#225;tico
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Con formato automático, un servicio de lenguaje inserta automáticamente un fragmento del código cuando un usuario empieza a escribir una construcción conocida del código.  
  
## Comportamiento de formato automático  
 Por ejemplo, cuando se escribe `if`, el servicio de lenguaje inserta automáticamente las llaves, o si presiona la tecla ENTRAR, el servicio de lenguaje fuerza el punto de inserción en la nueva línea al nivel de sangría adecuado, dependiendo de si la línea anterior abre un nuevo ámbito.  
  
 El filtro del comando utilizado para el resto del servicio de lenguaje también se puede utilizar para el formato automático.  También puede resaltar las llaves llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## Vea también  
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)