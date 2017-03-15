---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::put_registerValue (método)"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

establece el valor de un registro.  
  
## Sintaxis  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Parámetros  
 `index`  
 \[in\]  Un valor de enumeración de [CV\_HREG\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-hreg-e.md) que especifica el registro para escribir.  
  
 `NewVal`  
 \[in\]  El nuevo valor del registro.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 A pesar del tamaño del valor, una implementación debe almacenar sólo lo el registro contiene normalmente.  Por ejemplo, un registro de 8 bits llevaría a cabo únicamente los 8 bits inferiores del valor especificado.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-hreg-e.md)