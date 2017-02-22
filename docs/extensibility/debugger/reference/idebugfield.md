---
title: "IDebugField | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField"
helpviewer_keywords: 
  - "Interfaz IDebugField"
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un campo, es decir, una descripción de un símbolo o tipo.  
  
## Sintaxis  
  
```  
IDebugField : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz como clase base para todos los campos.  
  
## Notas para los llamadores  
 esta interfaz es la clase base para todos los campos.  Según el valor devuelto de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), esta interfaz puede devolver interfaces especializadas mediante [QueryInterface](/visual-cpp/atl/queryinterface).  Además, muchas interfaces devuelven objetos de `IDebugField` de varios métodos.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugField`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|obtiene la información mostrable sobre el símbolo o el tipo.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtiene el tipo de campo.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|obtiene el tipo de campo.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtiene el contenedor del campo.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtiene la dirección del campo.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtiene el tamaño de un campo, en bytes.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Gets extendidas información sobre un campo.|  
|[Igual](../../../extensibility/debugger/reference/idebugfield-equal.md)|compara dos campos.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtiene la información de la independientes del tipo sobre el símbolo o el tipo.|  
  
## Comentarios  
 Un tipo es equivalente al lenguaje `typedef`de C\/C\+\+.  
  
 En el ejemplo siguiente del lenguaje C\+\+, `weather` es un tipo de clase, y `sunny` y `stormy` son símbolos:  
  
```cpp#  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Si un campo representa un símbolo o un tipo puede ser determinado llamando a [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) y examina el resultado de [FIELD\_KIND](../../../extensibility/debugger/reference/field-kind.md) .  Si se establece el bit de `FIELD_KIND_TYPE` , el campo es un tipo y, si se establece el bit de `FIELD_KIND_SYMBOL` , es un símbolo.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)