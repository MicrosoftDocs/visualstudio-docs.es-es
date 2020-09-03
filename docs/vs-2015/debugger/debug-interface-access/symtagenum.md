---
title: SymTagEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1578d88265769414f68964e28d3426ffcc62f9e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193515"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el tipo de símbolo.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
## <a name="elements"></a>Elementos  
 `SymTagNull`  
 Indica que el símbolo no tiene ningún tipo.  
  
 `SymTagExe`  
 Indica que el símbolo es un archivo. exe. Solo hay un `SymTagExe` símbolo por almacén de símbolos. Sirve como ámbito global y no tiene un elemento primario léxico.  
  
 `SymTagCompiland`  
 Indica el símbolo de compilación para cada componente de compilación del almacén de símbolos. En el caso de las aplicaciones nativas, `SymTagCompiland` los símbolos se corresponden con los archivos objeto vinculados a la imagen. En el caso de algunos tipos de imágenes del lenguaje intermedio de Microsoft (MSIL), hay una operación de compilación por clase.  
  
 `SymTagCompilandDetails`  
 Indica que el símbolo contiene atributos extendidos de la operación de compilación. La recuperación de estas propiedades puede requerir la carga de símbolos de compilación.  
  
 `SymTagCompilandEnv`  
 Indica que el símbolo es una cadena de entorno definida para la compilación.  
  
 `SymTagFunction`  
 Indica que el símbolo es una función.  
  
 `SymTagBlock`  
 Indica que el símbolo es un bloque anidado.  
  
 `SymTagData`  
 Indica que el símbolo es datos.  
  
 `SymTagAnnotation`  
 Indica que el símbolo es para una anotación de código. Los elementos secundarios de este símbolo son cadenas de datos constantes ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). La mayoría de los clientes omiten este símbolo.  
  
 `SymTagLabel`  
 Indica que el símbolo es una etiqueta.  
  
 `SymTagPublicSymbol`  
 Indica que el símbolo es un símbolo público. En el caso de las aplicaciones nativas, este símbolo es el símbolo externo COFF encontrado al vincular la imagen.  
  
 `SymTagUDT`  
 Indica que el símbolo es un tipo definido por el usuario (estructura, clase o unión).  
  
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
 Indica que el símbolo es `typedef` , es decir, un alias de otro tipo.  
  
 `SymTagBaseClass`  
 Indica que el símbolo es una clase base de un tipo definido por el usuario.  
  
 `SymTagFriend`  
 Indica que el símbolo es un amigo de un tipo definido por el usuario.  
  
 `SymTagFunctionArgType`  
 Indica que el símbolo es un argumento de función.  
  
 `SymTagFuncDebugStart`  
 Indica que el símbolo es la ubicación final del código de prólogo de la función.  
  
 `SymTagFuncDebugEnd`  
 Indica que el símbolo es la ubicación inicial del código epílogo de la función.  
  
 `SymTagUsingNamespace`  
 Indica que el símbolo es un nombre de espacio de nombres, activo en el ámbito actual.  
  
 `SymTagVTableShape`  
 Indica que el símbolo es una descripción de la tabla virtual.  
  
 `SymTagVTable`  
 Indica que el símbolo es un puntero de tabla virtual.  
  
 `SymTagCustom`  
 Indica que el símbolo es un símbolo personalizado y no lo interpreta DIA.  
  
 `SymTagThunk`  
 Indica que el símbolo es un código thunk que se usa para compartir datos entre 16 y 32 bits.  
  
 `SymTagCustomType`  
 Indica que el símbolo es un símbolo del compilador personalizado.  
  
 `SymTagManagedType`  
 Indica que el símbolo está en metadatos.  
  
 `SymTagDimension`  
 Indica que el símbolo es una matriz multidimensional de FORTRAN.  
  
 `SymTagCallSite`  
 Indica que el símbolo representa el sitio de la llamada.  
  
 `SymTagInlineSite`  
 Indica que el símbolo representa el sitio en línea.  
  
 `SymTagBaseInterface`  
 Indica que el símbolo es una interfaz base.  
  
 `SymTagVectorType`  
 Indica que el símbolo es un tipo de vector.  
  
 `SymTagMatrixType`  
 Indica que el símbolo es un tipo de matriz.  
  
 `SymTagHLSLType`  
 Indica que el símbolo es un tipo de lenguaje de sombreador de alto nivel.  
  
## <a name="remarks"></a>Comentarios  
 Todos los símbolos de un archivo de depuración tienen una etiqueta de identificación que especifica el tipo del símbolo.  
  
 Los valores de esta enumeración son devueltos por una llamada al método [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .  
  
 Los valores de esta enumeración se pasan a los métodos siguientes para limitar el ámbito de la búsqueda a un tipo de símbolo específico:  
  
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession:: findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession:: findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession:: findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession:: findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession:: findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession:: findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession:: Findchildren (](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
