---
title: Jerarquía de clases de tipos de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c42ea4bb2d5c2ad91538bec8b31774a5a41aa4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745456"
---
# <a name="class-hierarchy-of-symbol-types"></a>Jerarquía de clases de tipos de símbolos
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

## <a name="see-also"></a>Vea también
- [Enumeración CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)
- [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)