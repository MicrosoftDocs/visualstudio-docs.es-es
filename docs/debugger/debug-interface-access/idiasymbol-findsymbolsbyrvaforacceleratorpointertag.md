---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de los símbolos incluidos en esta función de código auxiliar en una dirección relativa virtual especificada.  
  
## Sintaxis  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Parámetros  
 `tagValue`  
 \[in\] se encuentra el valor de etiqueta del puntero de El que el símbolo de pointee registra.  
  
 `rva`  
 \[in\] rva a El que se utiliza para filtrar los símbolos que corresponden a la variable de pointee con el valor de etiqueta especificado.  
  
 `ppResult`  
 \[out\] puntero A un puntero de interfaz de `IDiaEnumSymbols` inicializar con el resultado.  
  
## Valor devuelto  
 Si es correcto, especificado `S_OK`; si no, especificado `S_FALSE` o un código de error.  
  
## Comentarios  
 Llame a este método solo en una interfaz de `IDiaSymbol` correspondiente a una función de código auxiliar de aceleradores.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)