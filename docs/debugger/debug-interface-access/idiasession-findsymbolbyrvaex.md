---
title: "IDiaSession::findSymbolByRVAEx | Microsoft Docs"
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
  - "IDiaSession::findSymbolByRVAEx (método)"
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección virtual y un \(RVA\) desplazamiento relativos especificados.  
  
## Sintaxis  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### Parámetros  
 `rva`  
 \[in\]  especifica el RVA.  
  
 `symtag`  
 \[in\]  Tipo de token para encontrar.  los valores se toman de la enumeración de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) .  
  
 `ppSymbol`  
 \[out\]  Devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el token recuperado.  
  
 `displacement`  
 \[out\]  Devuelve un valor que especifica un desplazamiento de dirección virtual relativa especificada en `rva`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md)