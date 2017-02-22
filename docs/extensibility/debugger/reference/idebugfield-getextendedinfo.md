---
title: "IDebugField::GetExtendedInfo | Microsoft Docs"
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
  - "IDebugField::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugField::GetExtendedInfo (método)"
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugField::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método obtiene la información extendida sobre un campo.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```c#  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### Parámetros  
 `guidExtendedInfo`  
 \[in\]  Selecciona la información volver.  Los valores válidos son:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`guidConstantValue`|El valor como una secuencia de bytes.|  
|`guidConstantType`|El tipo como signatura de tipo.|  
  
 `prgBuffer`  
 \[out\]  Devuelve información extendida.  
  
 `pdwLen`  
 \[in, out\]  Devuelve el tamaño de la información extendida, en bytes.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Actualmente, este método sólo devuelve el tipo o el valor de una constante.  El llamador debe liberar el búfer devuelto en `prgBuffer` llamando a la función de `CoTaskMemFree` COM \(C\+\+\) o <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> \(C\#\).  
  
## Vea también  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)