---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame::get_rawLVarInstanceValue (método)"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

este método recupera el valor de la variable local especificada como bytes sin formato.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### Parámetros  
 `pInstance`  
 \[in\]  un objeto de `IDiaLVarInstance` que representa una instancia de la variable local para obtener el valor para.  
  
 `cbDataMax`  
 \[in\]  El número de bytes máximo del búfer al que `pbData`.  Puede ser un máximo de 8 bytes \(`sizeof(ULONGLONG)`\).  
  
 `pcbData`  
 \[out\]  devuelve el número de bytes real almacenados en el búfer.  
  
 `pbData`  
 \[out\]  un búfer que se completará con datos.  Su valor no puede ser `NULL`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)