---
title: "BP_LOCATION_TYPE | Microsoft Docs"
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
  - "BP_LOCATION_TYPE"
helpviewer_keywords: 
  - "Estructura BP_LOCATION_TYPE"
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el tipo de ubicación de punto de interrupción para una solicitud de punto de interrupción.  
  
## Sintaxis  
  
```cpp#  
enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
typedef DWORD BP_LOCATION_TYPE;  
```  
  
```c#  
public enum enum_BP_LOCATION_TYPE {   
   BPLT_NONE               = 0x00000000,  
   BPLT_FILE_LINE          = 0x00010000,  
   BPLT_FUNC_OFFSET        = 0x00020000,  
   BPLT_CONTEXT            = 0x00030000,  
   BPLT_STRING             = 0x00040000,  
   BPLT_ADDRESS            = 0x00050000,  
   BPLT_RESOLUTION         = 0x00060000,  
   BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,  
   BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,  
   BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,  
   BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,  
   BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,  
   BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,  
   BPLT_TYPE_MASK          = 0x0000FFFF,  
   BPLT_LOCATION_TYPE_MASK = 0xFFFF0000  
};  
```  
  
## Members  
 BPLT\_NONE  
 No especifica ninguna ubicación de punto de interrupción.  
  
 BPLT\_FILE\_LINE  
 Especifica el tipo de ubicación de punto de interrupción como línea del archivo.  
  
 BPLT\_FUNC\_OFFSET  
 Especifica el tipo de ubicación de punto de interrupción como un desplazamiento de la función.  
  
 BPLT\_CONTEXT  
 Especifica el tipo de ubicación de punto de interrupción como contexto.  
  
 BPLT\_STRING  
 Especifica el tipo de ubicación de punto de interrupción como cadena.  
  
 BPLT\_ADDRESS  
 Especifica el tipo de ubicación de punto de interrupción como dirección.  
  
 BPLT\_RESOLUTION  
 Especifica el tipo de ubicación de punto de interrupción como resolución.  
  
 BPLT\_CODE\_FILE\_LINE  
 Especifica el tipo de ubicación de punto de interrupción como una línea de código fuente.  
  
 BPLT\_CODE\_FUNC\_OFFSET  
 Especifica el tipo de ubicación de punto de interrupción como un desplazamiento de la función de código.  
  
 BPLT\_CODE\_CONTEXT  
 Especifica el tipo de ubicación de punto de interrupción como contexto del código.  
  
 BPLT\_CODE\_STRING  
 Especifica el tipo de ubicación de punto de interrupción como cadena de código.  
  
 BPLT\_CODE\_ADDRESS  
 Especifica el tipo de ubicación de punto de interrupción como código de dirección.  
  
 BPLT\_DATA\_STRING  
 Especifica el tipo de ubicación de punto de interrupción como una cadena de los datos.  
  
 BPLT\_TYPE\_MASK  
 Especifica una máscara de bits, para poder extraer el tipo de punto de interrupción por valor.  
  
 BPLT\_LOCATION\_TYPE\_MASK  
 Especifica una máscara de bits, para poder extraer el tipo de ubicación de punto de interrupción por valor.  
  
## Comentarios  
 Pasado como parámetro al método de [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md) .  
  
 Constituyen un tipo de ubicación de punto de interrupción de un tipo de punto de interrupción y un tipo de ubicación.  Esto significa que un tipo de ubicación de punto de interrupción nunca es simplemente un tipo de punto de interrupción \(por ejemplo,`BPT_CODE`\) o un tipo de ubicación \(por ejemplo,`BPLT_FILE_LINE`\).  Las constantes predefinidas para todos los tipos de ubicación de punto de interrupción admitidos actualmente se incluyen en esta enumeración \(`BPLT_CODE_FILE_LINE` con `BPLT_DATA_STRING`\).  
  
 `BPT_CODE` y `BPT_DATA` son miembros de la enumeración [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md).  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)   
 [BP\_TYPE](../../../extensibility/debugger/reference/bp-type.md)