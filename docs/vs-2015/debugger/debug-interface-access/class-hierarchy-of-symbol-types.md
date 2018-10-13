---
title: Jerarquía de tipos de símbolos de clases | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
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
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6fc7ee76ae8f7b1490d61cc0cc0022b719b0d7a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284042"
---
# <a name="class-hierarchy-of-symbol-types"></a>Jerarquía de clases de tipos de símbolos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la tabla siguiente describe los tipos de símbolos en la jerarquía de clases.  
  
## <a name="symbol-types"></a>Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Símbolo que se usa para representar cada clase, estructura y unión.|  
|[Enumeración (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Símbolos para los tipos enumerados.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Símbolo de tipos de puntero.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Símbolo de tipos de matriz.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Símbolos para los tipos base|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Símbolo que presenta los nombres de otros tipos.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Símbolo que se usa para cada clase base de un tipo definido por el usuario (UDT).|  
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Símbolo de clases y funciones friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Símbolo para cada firma de función única.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Símbolo para cada parámetro a una función.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Símbolos para el tamaño de la tabla virtual.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Símbolo de una tabla virtual.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Símbolo de tipo definido por el proveedor.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Símbolo de un tipo definido en metadatos.|  
|[Dimensión](../../debugger/debug-interface-access/dimension.md)|Símbolo de dimensiones de la matriz.|  
  
> [!NOTE]
>  Cada símbolo puede tener propiedades que contienen información acerca de los símbolos, así como referencias a otros símbolos. Estas propiedades se muestran en los temas individuales de símbolos.  
  
## <a name="see-also"></a>Vea también  
 [CV_access_e (enumeración)](../../debugger/debug-interface-access/cv-access-e.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)



