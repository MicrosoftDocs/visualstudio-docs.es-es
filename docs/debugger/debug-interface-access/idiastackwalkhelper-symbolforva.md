---
title: "IDiaStackWalkHelper::symbolForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper::symbolForVA (método)"
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el token que contiene la dirección virtual especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### Parámetros  
 `va`  
 \[in\]  La dirección virtual contenida en el token solicitado.  El token debe ser `SymTagFunctionType` \(un valor de enumeración de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).  
  
 `ppSymbol`  
 \[out\]  un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el símbolo en la dirección especificada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)