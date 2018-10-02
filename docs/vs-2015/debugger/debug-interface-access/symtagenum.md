---
title: SymTagEnum | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d90eac40bc6c64f83c1b55c2f0dd056e9aa9def
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581955"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [SymTagEnum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/symtagenum).  
  
Especifica el tipo de símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum SymTagEnum {   
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
  
## <a name="elements"></a>Elementos  
 `SymTagNull`  
 Indica que el símbolo no tiene ningún tipo.  
  
 `SymTagExe`  
 Indica que el símbolo es un archivo .exe. Solo hay un `SymTagExe` símbolo por el almacén de símbolos. Actúa como el ámbito global y no tiene un elemento primario léxico.  
  
 `SymTagCompiland`  
 Indica el símbolo de la operación de compilación para cada componente de la operación de compilación del almacén de símbolos. Para aplicaciones nativas, `SymTagCompiland` símbolos corresponden a los archivos objeto vinculados en la imagen. Para algunos tipos de imágenes de lenguaje intermedio de Microsoft (MSIL), hay una operación de compilación por clase.  
  
 `SymTagCompilandDetails`  
 Indica que el símbolo contiene atributos extendidos de la operación de compilación. Recuperar estas propiedades puede requerir la carga de símbolos de la operación de compilación.  
  
 `SymTagCompilandEnv`  
 Indica que el símbolo es una cadena de entorno definida para la operación de compilación.  
  
 `SymTagFunction`  
 Indica que el símbolo es una función.  
  
 `SymTagBlock`  
 Indica que el símbolo es un bloque anidado.  
  
 `SymTagData`  
 Indica que el símbolo de datos.  
  
 `SymTagAnnotation`  
 Indica que el símbolo de una anotación de código. Los elementos secundarios de este símbolo son cadenas de datos constantes (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La mayoría de los clientes pasar por alto este símbolo.  
  
 `SymTagLabel`  
 Indica que el símbolo es una etiqueta.  
  
 `SymTagPublicSymbol`  
 Indica que el símbolo es un símbolo público. Para aplicaciones nativas, este símbolo es el símbolo externo COFF al vincular la imagen.  
  
 `SymTagUDT`  
 Indica que el símbolo es un tipo definido por el usuario (estructura, unión o clase).  
  
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
 Indica que el símbolo es un `typedef`, es decir, un alias para otro tipo.  
  
 `SymTagBaseClass`  
 Indica que el símbolo es una clase base de un tipo definido por el usuario.  
  
 `SymTagFriend`  
 Indica que el símbolo es un elemento friend de un tipo definido por el usuario.  
  
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
 Indica que el símbolo es un puntero a la tabla virtual.  
  
 `SymTagCustom`  
 Indica que el símbolo es un símbolo personalizado y no interpreta DIA.  
  
 `SymTagThunk`  
 Indica que el símbolo es un código thunk que se utiliza para compartir datos entre 16 y el código de 32 bits.  
  
 `SymTagCustomType`  
 Indica que el símbolo es un símbolo personalizado del compilador.  
  
 `SymTagManagedType`  
 Indica que el símbolo es en los metadatos.  
  
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
  
## <a name="remarks"></a>Comentarios  
 Todos los símbolos dentro de un archivo de depuración tienen una etiqueta de identificación que especifica el tipo del símbolo.  
  
 Los valores de esta enumeración se devuelven mediante una llamada a la [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método.  
  
 Los valores de esta enumeración se pasan a los métodos siguientes para limitar el ámbito de la búsqueda a un tipo de símbolo específico:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [Findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [Findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [Findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [Findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [Findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



