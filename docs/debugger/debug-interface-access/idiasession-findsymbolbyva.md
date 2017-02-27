---
title: "IDiaSession::findSymbolByVA | Microsoft Docs"
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
  - "IDiaSession::findSymbolByVA (método)"
ms.assetid: 0350df23-9a5d-4e8d-8c26-7f571d8fb1af
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findSymbolByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección virtual especificada.  
  
## Sintaxis  
  
```cpp#  
HRESULT findSymbolByVA (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parámetros  
 `va`  
 \[in\]  Especifica la dirección virtual.  
  
 `symtag`  
 \[in\]  Tipo de token para encontrar.  los valores se toman de la enumeración de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 \[out\]  Devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el token recuperado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByVA( va, SymTagFunction, &pFunc );  
```  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)