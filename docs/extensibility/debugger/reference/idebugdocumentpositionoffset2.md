---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
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
  - "Interfaz IDebugDocumentPositionOffset2"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Representa una posición en un archivo de código fuente como desplazamiento de caracteres.  
  
## Sintaxis  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## Notas para los implementadores  
 Implementado por el IDE y usado por los motores de depuración.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugDocumentPositionOffset2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera el intervalo para la posición del documento actual.|  
  
## Comentarios  
 Esto devuelve la misma información que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) pero en desplazamientos de `char` desde el principio del documento.  Esto muestra el documento como existiría en un disco, es decir, una matriz unidimensional de caracteres, en lugar de la línea y la información de la columna que se devuelve normalmente.  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)