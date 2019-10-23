---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738511"
---
# <a name="symtagenum"></a>SymTagEnum
Especifica el tipo de símbolo.

## <a name="syntax"></a>Sintaxis

```C++
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
`SymTagNull` indica que el símbolo no tiene ningún tipo.

`SymTagExe` indica que el símbolo es un archivo. exe. Solo hay un símbolo de `SymTagExe` por almacén de símbolos. Sirve como ámbito global y no tiene un elemento primario léxico.

`SymTagCompiland` indica el símbolo de compilación de cada componente de compilación del almacén de símbolos. En el caso de las aplicaciones nativas, los símbolos de `SymTagCompiland` corresponden a los archivos objeto vinculados a la imagen. En el caso de algunos tipos de imágenes del lenguaje intermedio de Microsoft (MSIL), hay una operación de compilación por clase.

`SymTagCompilandDetails` indica que el símbolo contiene atributos extendidos de la operación de compilación. La recuperación de estas propiedades puede requerir la carga de símbolos de compilación.

`SymTagCompilandEnv` indica que el símbolo es una cadena de entorno definida para la compilación.

`SymTagFunction` indica que el símbolo es una función.

`SymTagBlock` indica que el símbolo es un bloque anidado.

`SymTagData` indica que el símbolo es datos.

`SymTagAnnotation` indica que el símbolo es para una anotación de código. Los elementos secundarios de este símbolo son cadenas de datos constantes (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La mayoría de los clientes omiten este símbolo.

`SymTagLabel` indica que el símbolo es una etiqueta.

`SymTagPublicSymbol` indica que el símbolo es un símbolo público. En el caso de las aplicaciones nativas, este símbolo es el símbolo externo COFF encontrado al vincular la imagen.

`SymTagUDT` indica que el símbolo es un tipo definido por el usuario (estructura, clase o unión).

`SymTagEnum` indica que el símbolo es una enumeración.

`SymTagFunctionType` indica que el símbolo es un tipo de firma de función.

`SymTagPointerType` indica que el símbolo es un tipo de puntero.

`SymTagArrayType` indica que el símbolo es un tipo de matriz.

`SymTagBaseType` indica que el símbolo es un tipo base.

`SymTagTypedef` indica que el símbolo es un `typedef`, es decir, un alias para otro tipo.

`SymTagBaseClass` indica que el símbolo es una clase base de un tipo definido por el usuario.

`SymTagFriend` indica que el símbolo es un amigo de un tipo definido por el usuario.

`SymTagFunctionArgType` indica que el símbolo es un argumento de función.

`SymTagFuncDebugStart` indica que el símbolo es la ubicación final del código de prólogo de la función.

`SymTagFuncDebugEnd` indica que el símbolo es la ubicación inicial del código epílogo de la función.

`SymTagUsingNamespace` indica que el símbolo es un nombre de espacio de nombres, activo en el ámbito actual.

`SymTagVTableShape` indica que el símbolo es una descripción de la tabla virtual.

`SymTagVTable` indica que el símbolo es un puntero de tabla virtual.

`SymTagCustom` indica que el símbolo es un símbolo personalizado y no lo interpreta DIA.

`SymTagThunk` indica que el símbolo es un código thunk que se usa para compartir datos entre 16 y 32 bits.

`SymTagCustomType` indica que el símbolo es un símbolo del compilador personalizado.

`SymTagManagedType` indica que el símbolo está en metadatos.

`SymTagDimension` indica que el símbolo es una matriz multidimensional de FORTRAN.

`SymTagCallSite` indica que el símbolo representa el sitio de la llamada.

`SymTagInlineSite` indica que el símbolo representa el sitio en línea.

`SymTagBaseInterface` indica que el símbolo es una interfaz base.

`SymTagVectorType` indica que el símbolo es un tipo de vector.

`SymTagMatrixType` indica que el símbolo es un tipo de matriz.

`SymTagHLSLType` indica que el símbolo es un tipo de lenguaje de sombreador de alto nivel.

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

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
