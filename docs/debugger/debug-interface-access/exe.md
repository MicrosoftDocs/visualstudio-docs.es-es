---
title: "Exe | Microsoft Docs"
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
  - "archivos .dll"
  - "Exe (símbolo)"
  - "archivos .exe"
  - "archivos ejecutables, símbolo Exe"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Exe es el único símbolo sin un elemento primario léxico o clase, como representa el ámbito global del archivo .exe o .dll.  Sólo hay un símbolo con la etiqueta de `SymTagExe` por archivo.  el método de [IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) devuelve el símbolo.  
  
## Propiedades  
 La tabla siguiente se muestran las propiedades que son válidas para este tipo de token.  
  
|Propiedad.|Tipo de datos|Descripción|  
|----------------|-------------------|-----------------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Edad de este archivo ejecutable.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` de este archivo ejecutable.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` si el archivo de símbolos asociado a este archivo ejecutable contiene C Types \(solo en el diámetro SDK v8.0 o posterior\).|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` si símbolos privados se han eliminado del archivo de símbolos asociado a este archivo ejecutable \(solo en el diámetro SDK v8.0 o posterior\).|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|valor que indica el destino CPU \(uno de los valores de [CV\_CPU\_TYPE\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-cpu-type-e.md) \).|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nombre del archivo .exe.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Firma del ejecutable.|  
|[IDiaSymbol::get\_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Ruta de acceso completa para el archivo .pdb o de .dbg del archivo .exe.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolos.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|devuelve `SymTagExe` \(uno de los valores de [SymTagEnum \(Enumeración\)](../../debugger/debug-interface-access/symtagenum.md) \).|  
  
## Vea también  
 [IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)