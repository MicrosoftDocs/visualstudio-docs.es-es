---
title: "BP_RESOLUTION_LOCATION | Microsoft Docs"
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
  - "BP_RESOLUTION_LOCATION"
helpviewer_keywords: 
  - "Estructura BP_RESOLUTION_LOCATION"
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_RESOLUTION_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica la estructura de la ubicación de la resolución de punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
struct _BP_RESOLUTION_LOCATION {  
   BP_TYPE bpType;  
   union {  
      BP_RESOLUTION_CODE bpresCode;  
      BP_RESOLUTION_DATA bpresData;  
      int                unused;  
   } bpResLocation;  
} BP_RESOLUTION_LOCATION;  
```  
  
```c#  
public struct BP_RESOLUTION_LOCATION {  
   public uint bpType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public uint   unionmember4;  
};  
```  
  
## Members  
 `bpType`  
 Un valor de enumeración de [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md) que especifica cómo interpretar la unión de `bpResLocation` o miembros de `unionmemberX` .  
  
 `bpResLocation.bpresCode`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) si `bpType` \= `BPT_CODE`.  
  
 `bpResLocation.bpresData`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) si `bpType` \= `BPT_DATA`.  
  
 `bpResLocation.unused`  
 \[C\+\+ sólo\] marcador de A.  
  
 `unionmember1`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
 `unionmember2`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
 `unionmember3`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
 `unionmember4`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
## Comentarios  
 esta estructura es un miembro de las estructuras de [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) y de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .  
  
 \[C\# solo\] interpretan los miembros de El `unionmemberX` según la tabla siguiente.  Busque bajar la columna izquierda el valor de `bpType` recorre para determinar lo que representa cada miembro de `unionmemberX` y dan forma `unionmemberX` en consecuencia.  Vea el ejemplo para que una forma interpreta esta estructura en C\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPT_DATA`|`string` \(expresión de datos\)|`string` \(nombre de función\)|`string` \(nombre de imagen\)|`enum_BP_RES_DATA_FLAGS`|  
  
## Ejemplo  
 este ejemplo muestra cómo interpretar la estructura de `BP_RESOLUTION_LOCATION` en C\#.  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_RESOLUTION_LOCATION bprl)  
        {  
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)  
            {  
                 IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
            }  
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)  
            {  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;  
            }  
        }  
    }  
}  
```  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)   
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)   
 [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)