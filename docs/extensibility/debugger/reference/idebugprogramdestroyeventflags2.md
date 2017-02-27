---
title: "IDebugProgramDestroyEventFlags2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugProgramDestroyEventFlags2"
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite a un motor de depuración para invalidar el comportamiento predeterminado de la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]al finalizar una sesión de depuración.  
  
## Sintaxis  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa por los motores de depuración.  Es útil para los hosts que pueden crear y destruir varios programas sobre la duración de un proceso.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugProgramDestroyEventFlags2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera el programa destruyen los marcadores.|  
  
## Comentarios  
 El comportamiento predeterminado de la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] es volver a los programas del modo de diseño después de todo ha enviado un programa destruye evento.  Esta interfaz permite a un motor de depuración para cambiar el comportamiento.  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll