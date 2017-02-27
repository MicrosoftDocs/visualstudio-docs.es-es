---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Devuelve una enumeración de los símbolos para los marcos flotantes correspondiente al nombre especificado de la función inline.  
  
## Sintaxis  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parámetros  
 `name`  
 \[in\] nombre de función del incluido a El que se buscará.  
  
 `option`  
 \[in\] opciones de búsqueda de nombre de utilizar al buscar los marcos de punto flotante que corresponden a `name`.  Para obtener más información, vea [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 \[out\] puntero A un puntero de interfaz de `IDiaEnumSymbols` inicializar con el resultado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Las búsquedas de esta función para los inlinees desde dentro del código auxiliar de aceleradores funcionan.  Omite los registros del procedimiento de C\+\+ nativo.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)