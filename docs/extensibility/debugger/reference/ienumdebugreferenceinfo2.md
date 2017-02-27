---
title: "IEnumDebugReferenceInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugReferenceInfo2"
helpviewer_keywords: 
  - "IEnumDebugReferenceInfo2"
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugReferenceInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se enumeran las estructuras de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
## Sintaxis  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz como parte de su compatibilidad con las referencias a objetos en memoria.  Esta interfaz se debe implementar solo si se admiten las referencias.  
  
## Notas para los llamadores  
 Visual Studio llama [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IEnumDebugReferenceInfo2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Recupera un número especificado de estructuras de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Omite un número especificado de estructuras de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) en la secuencia de la enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtiene el número de estructuras de [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) de un enumerador.|  
  
## Comentarios  
 Una referencia es esencialmente un tipo y una dirección, mientras que una propiedad es un nombre, tipo, y una dirección.  Una referencia se conserva cuando el objeto denominado existe en memoria.  Vea [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) para obtener más información.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)