---
title: "M&#243;dulos | Microsoft Docs"
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
  - "módulos"
  - "depurar [SDK de depuración], módulos"
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# M&#243;dulos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En términos de arquitectura del depurador, **un módulo**:  
  
-   Es un contenedor físico de código, como un archivo ejecutable o DLL.  
  
-   Puede volver a cargar los símbolos y describirse.  Las descripciones de módulo se muestran en la ventana módulos del IDE.  
  
-   Se representa mediante una interfaz de [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , crea un motor de depuración para describir el módulo.  
  
## Vea también  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)