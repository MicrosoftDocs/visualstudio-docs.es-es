---
title: "IDiaSymbol::get_length | Microsoft Docs"
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
  - "IDiaSymbol::get_length (método)"
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSymbol::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el número de bits o de bytes de memoria utilizados por el objeto representado por este símbolo.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve el número de bytes o de bits de memoria utilizados por el objeto representado por este símbolo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 Si [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md) de símbolos es `LocIsBitField`, la longitud devuelta por este método está en bits; si no, la longitud en bytes para todos los demás tipos de ubicación.  
  
## Ejemplo  
  
```cpp#  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v7.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md)