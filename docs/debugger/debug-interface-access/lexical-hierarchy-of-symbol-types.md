---
title: Jerarquía léxica de tipos de símbolos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58c4ef49cb7eabae7608ce417e4f3d5ef99a8284
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Jerarquía léxica de tipos de símbolos
En la tabla siguiente muestra los tipos de símbolos en la jerarquía de léxica.  
  
## <a name="symbol-types"></a>Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|-----------------|-----------------|  
|[Anotación](../../debugger/debug-interface-access/annotation.md)|Especifica una ubicación anotada en el código de programa.|  
|[Bloque](../../debugger/debug-interface-access/block.md)|Especifica los ámbitos anidados en funciones.|  
|`Compiland`|Especifica un `compiland` vinculadas al archivo .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Especifica los datos de operación de compilación que se pueden requerir Cargando detalles adicionales de la operación de compilación y, por tanto, incurrir en tiempo de ejecución sobrecarga para recuperar.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Especifica las variables de entorno adicional importantes para la compilación de la operación de compilación.|  
|[Personalizado (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Especifica un símbolo definido por el usuario.|  
|[Datos (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Especifica dichas variables como parámetros, variables locales, las variables globales y los miembros de clase.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Especifica el ámbito global de los datos; corresponde a un archivo .exe o .dll completo.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Especifica una función que tiene un punto definido en qué tipo de depuración que se va a terminar.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Especifica una función que tiene un punto definido en qué depuración consiste en empezar.|  
|[Función (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Especifica una función.|  
|[Etiqueta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Especifica una ubicación en el código de programa.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Especifica un símbolo externo que aparece al compilar el programa ejecutable.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Especifica un `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Especifica un `namespace`identificador.|  
  
> [!NOTE]
>  Propiedades de símbolos adicionales pueden estar disponibles según el tipo de símbolo. Estas propiedades se muestran en los temas individuales de símbolos.  
  
## <a name="see-also"></a>Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md)