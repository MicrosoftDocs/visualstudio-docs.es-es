---
title: Jerarquía de tipos de símbolos de clases | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24371e1e09d3eb4404eac751cd4ef651afbfb7e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="class-hierarchy-of-symbol-types"></a>Jerarquía de clases de tipos de símbolos
La tabla siguiente describen los tipos de símbolos en la jerarquía de clases.  
  
## <a name="symbol-types"></a>Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Símbolo que se usa para representar cada clase, estructura y unión.|  
|[Enumeración (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Símbolos para los tipos enumerados.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Símbolo de tipos de puntero.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Símbolo de tipos de matriz.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Símbolo de tipos base|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Símbolo que presenta los nombres de otros tipos.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Símbolo que se usa para cada clase base de un tipo definido por el usuario (UDT).|  
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Símbolo de clases de confianza y las funciones friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Símbolo para cada firma de función única.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Símbolo para cada parámetro a una función.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Símbolo para el tamaño de la tabla virtual.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Símbolo de una tabla virtual.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Símbolo de tipo definido por el proveedor.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Símbolo de un tipo definido en los metadatos.|  
|[Dimensión](../../debugger/debug-interface-access/dimension.md)|Símbolo de dimensiones de la matriz.|  
  
> [!NOTE]
>  Cada símbolo puede tener propiedades que contienen información acerca de los símbolos, así como las referencias a otros símbolos. Estas propiedades se muestran en los temas individuales de símbolos.  
  
## <a name="see-also"></a>Vea también  
 [CV_access_e (enumeración)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)