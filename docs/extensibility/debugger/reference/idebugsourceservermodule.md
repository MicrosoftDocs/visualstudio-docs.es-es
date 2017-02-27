---
title: "IDebugSourceServerModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugSourceServerModule"
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Representa la información del servidor de origen que contenga un archivo PDB.  
  
## Sintaxis  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa por los motores del depurador y utilizada por la interfaz de usuario del depurador.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugSourceServerModule`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matriz de información del servidor de origen.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll