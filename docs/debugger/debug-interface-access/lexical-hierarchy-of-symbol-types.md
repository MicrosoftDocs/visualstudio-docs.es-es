---
title: Jerarquía léxica de tipos de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad782ddb9a88b492d03e2338f17d95fb7bfa4f79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738667"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Jerarquía léxica de tipos de símbolos
En la tabla siguiente se muestran los tipos de símbolo de la jerarquía léxica.

## <a name="symbol-types"></a>Tipos de símbolos

|Tipo de símbolo|Descripción|
|-----------------|-----------------|
|[Anotación](../../debugger/debug-interface-access/annotation.md)|Especifica una ubicación anotada en el código del programa.|
|[Bloque](../../debugger/debug-interface-access/block.md)|Especifica ámbitos anidados en funciones.|
|`Compiland`|Especifica un `compiland` vinculado al archivo. exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Especifica la compilación de datos que pueden requerir la carga de detalles de la compilación adicionales y, por tanto, provocar una sobrecarga en tiempo de ejecución para recuperar.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Especifica las variables de entorno adicionales significativas para la compilación de la compilación.|
|[Personalizado (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Especifica un símbolo definido por el usuario.|
|[Datos (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Especifica tales variables como parámetros, variables locales, variables globales y miembros de clase.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Especifica el ámbito global de los datos; corresponde a un archivo. exe o. dll completo.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Especifica una función que tiene un punto definido en el que la depuración va a finalizar.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Especifica una función que tiene un punto definido en el que se va a iniciar la depuración.|
|[Función (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Especifica una función.|
|[Etiqueta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Especifica una ubicación en el código del programa.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Especifica un símbolo externo que aparece al compilar el programa ejecutable.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Especifica un `thunk`.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Especifica un `namespace`identifier.|

> [!NOTE]
> Pueden estar disponibles propiedades de símbolos adicionales en función del tipo de símbolo. Estas propiedades se enumeran en los temas de símbolos individuales.

## <a name="see-also"></a>Vea también
- [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)