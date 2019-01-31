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
ms.openlocfilehash: 47c32bdeee62216c17c7557d6651e608953b73b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928989"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Jerarquía léxica de tipos de símbolos
En la tabla siguiente se muestra los tipos de símbolos en la jerarquía de léxica.  
  
## <a name="symbol-types"></a>Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|-----------------|-----------------|  
|[Anotación](../../debugger/debug-interface-access/annotation.md)|Especifica una ubicación anotada en el código de programa.|  
|[Bloque](../../debugger/debug-interface-access/block.md)|Especifica los ámbitos anidados en funciones.|  
|`Compiland`|Especifica un `compiland` vinculado con el archivo .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Especifica los datos de la operación de compilación que pueden requerir al cargar los detalles de la operación de compilación adicionales y, por tanto, se incurre en tiempo de ejecución sobrecarga para recuperar.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Especifica las variables de entorno adicionales importantes a la compilación de la operación de compilación.|  
|[Personalizado (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Especifica un símbolo definido por el usuario.|  
|[Datos (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Especifica estas variables como parámetros, variables locales, las variables globales y los miembros de clase.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Especifica el ámbito global de los datos; corresponde a un archivo .exe o .dll completo.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Especifica una función que tiene un punto definido en el que la depuración consiste en Finalizar.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Especifica una función que tiene un punto definido en el que la depuración que se va a comenzar.|  
|[Función (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Especifica una función.|  
|[Etiqueta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Especifica una ubicación en el código del programa.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Especifica un símbolo externo que aparece al compilar el programa ejecutable.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Especifica un `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Especifica un `namespace`identificador.|  
  
> [!NOTE]
>  Propiedades de símbolos adicionales pueden estar disponibles según el tipo de símbolo. Estas propiedades se muestran en los temas individuales de símbolos.  
  
## <a name="see-also"></a>Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)