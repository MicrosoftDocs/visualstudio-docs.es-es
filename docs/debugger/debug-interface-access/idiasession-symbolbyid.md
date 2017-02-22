---
title: "IDiaSession::symbolById | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::symbolById (método)"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un símbolo por su identificador único.  
  
## Sintaxis  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parámetros  
 `id`  
 \[in\]  identificador único.  
  
 `ppSymbol`  
 \[out\]  Devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el token recuperado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 el identificador especificado es un valor único utilizado internamente por el diámetro SDK para crear todos los símbolos únicos.  
  
 Este método se puede utilizar, por ejemplo, para recuperar el token que representa el tipo de otro símbolo \(vea el ejemplo\).  
  
## Ejemplo  
 Este ejemplo recupera [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el tipo de otro token.  este ejemplo muestra cómo utilizar el método de `symbolById` en la sesión.  Un enfoque más sencillo es llamar al método de [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) para recuperar el token de tipo directamente.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)