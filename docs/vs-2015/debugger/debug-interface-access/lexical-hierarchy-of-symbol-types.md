---
title: Jerarquía léxica de tipos de símbolos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e70b83046c41b13cb51324eb63e81b26a118a81f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842951"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Jerarquía léxica de tipos de símbolos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la tabla siguiente se muestran los tipos de símbolo de la jerarquía léxica.  
  
## <a name="symbol-types"></a>Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|-----------------|-----------------|  
|[Anotación](../../debugger/debug-interface-access/annotation.md)|Especifica una ubicación anotada en el código del programa.|  
|[Bloquear](../../debugger/debug-interface-access/block.md)|Especifica ámbitos anidados en funciones.|  
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
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Especifica un `thunk` .|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Especifica un `namespace` identificador.|  
  
> [!NOTE]
> Pueden estar disponibles propiedades de símbolos adicionales en función del tipo de símbolo. Estas propiedades se enumeran en los temas de símbolos individuales.  
  
## <a name="see-also"></a>Consulte también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Símbolos y etiquetas de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
