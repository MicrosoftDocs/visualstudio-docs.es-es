---
title: Símbolos y etiquetas de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738528"
---
# <a name="symbols-and-symbol-tags"></a>Símbolos y etiquetas de símbolo
La información de depuración de un programa compilado se almacena en el archivo de base de datos de programa (. pdb) como símbolos a los que se puede tener acceso mediante las API del SDK de Debug interface Access (DIA). Todos los símbolos tienen una propiedad [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) y [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . La propiedad `symTag` indica el tipo de símbolo tal y como se define en la enumeración de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) . La propiedad `symIndexId` es un valor `DWORD` que contiene el identificador único para cada instancia de un símbolo.

 Los símbolos también tienen propiedades que pueden especificar información adicional sobre el símbolo, así como referencias a otros símbolos, a menudo una [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Cuando se consulta una propiedad que contiene una referencia, la referencia se devuelve como un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Estas propiedades siempre se emparejan con otra propiedad con el mismo nombre pero con el sufijo "ID", por ejemplo, [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) y [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Las tablas de las [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md), la [jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)y la [jerarquía de clases de los tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) describen las propiedades de cada uno de los distintos tipos de símbolos. Estas propiedades pueden tener información relevante sobre las referencias o a otros símbolos. Dado que las propiedades de `*Id` son simplemente identificadores ordinales numéricos de sus propiedades relacionadas, se omiten en discusiones posteriores. Solo se hace referencia a ellos cuando sea necesario para la aclaración de los parámetros.

 Al intentar obtener acceso a la propiedad, si no se produce ningún error y se ha asignado un valor a la propiedad Symbol, el método "Get" de la propiedad devuelve `S_OK`. Un valor devuelto de `S_FALSE` indica que la propiedad no es válida para el símbolo actual.

## <a name="in-this-section"></a>En esta sección

[Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)

Describe los diferentes tipos de ubicaciones que puede tener un símbolo.

[Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Describe los tipos de símbolos que forman jerarquías léxicas como archivos, módulos y funciones.

[Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Describe los tipos de símbolos que corresponden a elementos de lenguaje diferentes, como clases, matrices y tipos de valor devueltos de función.

## <a name="see-also"></a>Vea también

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)