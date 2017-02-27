---
title: "BP_LOCATION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION"
helpviewer_keywords: 
  - "Unión BP_LOCATION"
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BP_LOCATION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el tipo de estructura utilizado para describir la ubicación del punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION {  
   BP_LOCATION_TYPE bpLocationType;  
   union {  
      BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;  
      BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;  
      BP_LOCATION_CODE_CONTEXT     bplocCodeContext;  
      BP_LOCATION_CODE_STRING      bplocCodeString;  
      BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;  
      BP_LOCATION_DATA_STRING      bplocDataString;  
      BP_LOCATION_RESOLUTION       bplocResolution;  
      DWORD                        unused;  
   } bpLocation;  
} BP_LOCATION;  
```  
  
```c#  
public struct BP_LOCATION {  
   public uint   bpLocationType;  
   public IntPtr unionmember1;  
   public IntPtr unionmember2;  
   public IntPtr unionmember3;  
   public IntPtr unionmember4;  
};  
```  
  
## Members  
 `bpLocationType`  
 Un valor de enumeración de [BP\_LOCATION\_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) utilizada para interpretar la unión de `bpLocation` o miembros de `unionmemberX` .  
  
 `bpLocation`.`bplocCodeFileLine`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) si `bpLocationType` \= `BPLT_CODE_FILE_LINE`.  
  
 `bpLocation.bplocCodeFuncOffset`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) si `bpLocationType` \= `BPLT_CODE_FUNC_OFFSET`.  
  
 `bpLocation.bplocCodeContext`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) si `bpLocationType` \= `BPLT_CODE_CONTEXT`.  
  
 `bpLocation.bplocCodeString`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) si `bpLocationType` \= `BPLT_CODE_STRING`.  
  
 `bpLocation.bplocCodeAddress`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) si `bpLocationType` \= `BPLT_CODE_ADDRESS`.  
  
 `bpLocation.bplocDataString`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) si `bpLocationType` \= `BPLT_DATA_STRING`.  
  
 `bpLocation.bplocResolution`  
 \[C\+\+ sólo\] Contiene la estructura de [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) si `bpLocationType` \= `BPLT_RESOLUTION`.  
  
 `unionmember1`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
 `unionmember2`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
 `unionmember3`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
 `unionmember4`  
 \[C\# solo\] vea las notas de cómo interpretar.  
  
## Comentarios  
 esta estructura es un miembro de las estructuras de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 \[C\# solo\] interpretan los miembros de El `unionmemberX` según la tabla siguiente.  Busque bajar la columna izquierda el valor de `bpLocationType` después busque a través de las demás columnas para determinar lo que representa cada miembro de `unionmemberX` y dan forma `unionmemberX` en consecuencia.  Vea el ejemplo para que una forma interpretar una parte de esta estructura en C\#.  
  
|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|  
|----------------------|--------------------|--------------------|--------------------|--------------------|  
|`BPLT_CODE_FILE_LINE`|`string` \(un contexto\)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|\-|\-|  
|`BPLT_CODE_FUNC_OFFSET`|`string` \(un contexto\)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|\-|\-|  
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|\-|\-|\-|  
|`BPLT_CODE_STRING`|`string` \(un contexto\)|`string` \(expresión condicional\)|\-|\-|  
|`BPLT_CODE_ADDRESS`|`string` \(un contexto\)|`string` \(dirección URL de módulo\)|`string` \(nombre de función\)|`string` \(dirección\)|  
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string` \(un contexto\)|`string` \(expresión de datos\)|`uint` \(número de elementos\)|  
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|\-|\-|\-|  
  
## Ejemplo  
 este ejemplo muestra cómo interpretar la estructura de `BP_LOCATION` en C\# para el tipo de `BPLT_DATA_STRING` .  Este tipo determinado muestra cómo interpretar los cuatro miembros de `unionmemberX` en todos los formatos posibles \(objeto, string, y número\).  
  
```c#  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(BP_LOCATION bp)  
        {  
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)  
            {  
                 IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);  
                 string context = Marshal.PtrToStringBSTR(bp.unionmember2);  
                 string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);  
                 uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);  
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
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)   
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)   
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)   
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)   
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)