---
title: "SymTagEnum | Microsoft Docs"
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
  - "SymTagEnum (enumeración)"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica el tipo de símbolo.  
  
## Sintaxis  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## Elementos \(Elements\)  
 `SymTagNull`  
 Indica que el símbolo no tiene tipo.  
  
 `SymTagExe`  
 Indica que el símbolo es un archivo .exe.  Sólo hay una `SymTagExe` símbolo por el almacén de símbolos.  Sirve como el ámbito global y no tiene un léxico principal.  
  
 `SymTagCompiland`  
 Indica el símbolo de la operación de compilación para cada componente de la operación de compilación del almacén de símbolos.  Para aplicaciones nativas, `SymTagCompiland` símbolos corresponden a los archivos de objeto vinculados en la imagen.  Para algunos tipos de imágenes de lenguaje intermedio de Microsoft \(MSIL\), hay una operación de compilación por clase.  
  
 `SymTagCompilandDetails`  
 Indica que el símbolo contiene los atributos extendidos de la operación de compilación.  Recuperar estas propiedades puede requerir la carga de símbolos de operación de compilación.  
  
 `SymTagCompilandEnv`  
 Indica que el símbolo es una cadena de entorno definida para la operación de compilación.  
  
 `SymTagFunction`  
 Indica que el símbolo es una función.  
  
 `SymTagBlock`  
 Indica que el símbolo es un bloque anidado.  
  
 `SymTagData`  
 Indica que el símbolo de datos.  
  
 `SymTagAnnotation`  
 Indica que el símbolo para una anotación del código.  Elementos secundarios de este símbolo son cadenas de datos constante \(`SymTagData`, `LocIsConstant`, `DataIsConstant`\).  La mayoría de los clientes pasar por alto este símbolo.  
  
 `SymTagLabel`  
 Indica que el símbolo es una etiqueta.  
  
 `SymTagPublicSymbol`  
 Indica que el símbolo es pública.  Para aplicaciones nativas, este símbolo es el símbolo externo de COFF encontrado al vincular la imagen.  
  
 `SymTagUDT`  
 Indica que el símbolo es un tipo definido por el usuario \(estructura, clase o unión\).  
  
 `SymTagEnum`  
 Indica que el símbolo es una enumeración.  
  
 `SymTagFunctionType`  
 Indica que el símbolo es un tipo de firma de función.  
  
 `SymTagPointerType`  
 Indica que el símbolo es un tipo de puntero.  
  
 `SymTagArrayType`  
 Indica que el símbolo es un tipo de matriz.  
  
 `SymTagBaseType`  
 Indica que el símbolo es un tipo base.  
  
 `SymTagTypedef`  
 Indica que el símbolo es un `typedef`, es decir, un alias de otro tipo.  
  
 `SymTagBaseClass`  
 Indica que el símbolo es una clase base de un tipo definido por el usuario.  
  
 `SymTagFriend`  
 Indica que el símbolo es un amigo de un tipo definido por el usuario.  
  
 `SymTagFunctionArgType`  
 Indica que el símbolo es un argumento de función.  
  
 `SymTagFuncDebugStart`  
 Indica que el símbolo es la ubicación final del código de prólogo de la función.  
  
 `SymTagFuncDebugEnd`  
 Indica que el símbolo es la ubicación de comienzo del código de epílogo de la función.  
  
 `SymTagUsingNamespace`  
 Indica que el símbolo es un nombre de espacio de nombres activo en el ámbito actual.  
  
 `SymTagVTableShape`  
 Indica que el símbolo es una descripción de la tabla virtual.  
  
 `SymTagVTable`  
 Indica que el símbolo es un puntero de la tabla virtual.  
  
 `SymTagCustom`  
 Indica que el símbolo es un símbolo personalizado y no se interpreta de diámetro.  
  
 `SymTagThunk`  
 Indica que el símbolo es un código thunk de utilizan para compartir datos entre 16 y 32 bits.  
  
 `SymTagCustomType`  
 Indica que el símbolo es un compilador personalizado.  
  
 `SymTagManagedType`  
 Indica que es el símbolo de metadatos.  
  
 `SymTagDimension`  
 Indica que el símbolo es una matriz multidimensional de FORTRAN.  
  
 `SymTagCallSite`  
 Indica que el símbolo representa el sitio de llamada.  
  
 `SymTagInlineSite`  
 Indica que el símbolo representa el sitio en línea.  
  
 `SymTagBaseInterface`  
 Indica que el símbolo es una interfaz base.  
  
 `SymTagVectorType`  
 Indica que el símbolo es un tipo de vector.  
  
 `SymTagMatrixType`  
 Indica que el símbolo es un tipo de matriz.  
  
 `SymTagHLSLType`  
 Indica que el símbolo es un tipo de lenguaje de sombreado de alto nivel.  
  
## Comentarios  
 Todos los símbolos dentro de un archivo de depuración tienen una etiqueta identificativa que especifica el tipo del símbolo.  
  
 Los valores de esta enumeración se devuelven mediante una llamada a la [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método.  
  
 Los valores de esta enumeración se pasan a los métodos siguientes para limitar el ámbito de la búsqueda a un tipo de símbolo específicas:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Requisitos  
 Encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)