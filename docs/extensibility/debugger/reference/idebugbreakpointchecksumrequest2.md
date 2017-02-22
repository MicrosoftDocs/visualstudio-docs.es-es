---
title: "IDebugBreakpointChecksumRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugBreakpointChecksumRequest2"
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Representa una suma de comprobación del documento para una solicitud de punto de interrupción.  
  
## Sintaxis  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## Notas para los implementadores  
 Implementa el paquete de depuración de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] y usado por los motores de depuración.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugBreakpointChecksumRequest2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera la suma de comprobación del documento para una solicitud de punto de interrupción según el identificador único del algoritmo de suma de comprobación para utilizar.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina si la suma de comprobación está habilitada para este documento.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll