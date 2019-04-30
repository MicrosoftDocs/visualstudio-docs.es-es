---
title: Jerarquía de tipos de símbolos de clases | Documentos de Microsoft
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
ms.openlocfilehash: bc9981d324fe61cd3afe6cce4bc08d7b9b686c7f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402618"
---
# <a name="class-hierarchy-of-symbol-types"></a>Jerarquía de clases de tipos de símbolos
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
> Cada símbolo puede tener propiedades que contienen información acerca de los símbolos, así como referencias a otros símbolos. Estas propiedades se muestran en los temas individuales de símbolos.

## <a name="see-also"></a>Vea también
- [Enumeración CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)
- [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)