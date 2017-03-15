---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::get_registerValue (método)"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el valor de un registro.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Parámetros  
 `index`  
 \[in\]  Un valor de especificar la enumeración de [CV\_HREG\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-hreg-e.md) de que registre para obtener el valor.  
  
 `pRetVal`  
 \[out\]  Devuelve el valor actual del registro.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 A pesar del tamaño del parámetro de `pRetVal` , una implementación debe almacenar sólo lo el registro contiene normalmente.  Por ejemplo, un registro de 8 bits contiene únicamente los 8 bits inferiores del valor especificado.  Este valor de 8 bits se expande a 64 bits cuando se cambia de este método.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-hreg-e.md)