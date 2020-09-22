---
title: Jerarquía de clases de tipos de símbolos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a7b3edb0262e3e2b4f0cde51b499e25b04aba51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843187"
---
# <a name="class-hierarchy-of-symbol-types"></a>Jerarquía de clases de tipos de símbolos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la tabla siguiente se describen los tipos de símbolo de la jerarquía de clases.  
  
## <a name="symbol-types"></a>Tipos de símbolos  
  
|Tipo de símbolo|Descripción|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Símbolo que se usa para representar cada clase, estructura y Unión.|  
|[Enumeración (Debug Interface Access SDK)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Símbolo para los tipos enumerados.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Símbolo para los tipos de puntero.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Símbolo para los tipos de matriz.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Símbolo para los tipos base|  
|[Typedef (Debug Interface Access SDK)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Símbolo que introduce nombres para otros tipos.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Símbolo que se usa para cada clase base de un tipo definido por el usuario (UDT).|  
|[Friend (Debug Interface Access SDK)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbol para las clases Friend y Friend functions.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbol para cada signatura de función única.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbol para cada parámetro de una función.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Símbolo del tamaño de la tabla virtual.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Símbolo de una tabla virtual.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Símbolo del tipo definido por el proveedor.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Símbolo para un tipo definido en los metadatos.|  
|[Dimensión](../../debugger/debug-interface-access/dimension.md)|Símbolo para las dimensiones de la matriz.|  
  
> [!NOTE]
> Cada símbolo puede tener propiedades que contienen información sobre el símbolo, así como referencias a otros símbolos. Estas propiedades se enumeran en los temas de símbolos individuales.  
  
## <a name="see-also"></a>Consulte también  
 [Enumeración CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
