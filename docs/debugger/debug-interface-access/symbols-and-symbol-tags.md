---
title: Los símbolos y etiquetas de símbolo | Documentos de Microsoft
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
ms.openlocfilehash: 6affc24a84ef4d008ece5f95e45a11eb70f33b4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854713"
---
# <a name="symbols-and-symbol-tags"></a>Símbolos y etiquetas de símbolo
Información de depuración sobre un programa compilado se almacena en el archivo de programa (.pdb) de la base de datos como los símbolos que son accesibles mediante la API del SDK de Debug Interface Access (DIA). Todos los símbolos tienen un [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) y un [Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) propiedad. El `symTag` propiedad indica el tipo de símbolo definido por el [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración. El `symIndexId` propiedad es un `DWORD` valor que contiene el identificador único para cada instancia de un símbolo.

 Los símbolos también tienen propiedades que pueden especificar la información adicional acerca de los símbolos, así como referencias a otros símbolos, más a menudo un [Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Al consultar una propiedad que contiene una referencia, se devuelve la referencia como un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto. Estas propiedades son siempre emparejadas con otra propiedad con el mismo nombre pero con sufijo con "Id", por ejemplo, [Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) y [Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Las tablas de [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md), [jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), y [jerarquía de tipos de símbolos de clase](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) describir las propiedades para cada uno de los diferentes tipos de símbolos. Estas propiedades pueden tener información relevante sobre o referencias a otros símbolos. Dado que el `*Id` las propiedades son identificadores ordinales simplemente numéricos de sus propiedades relacionadas, se omiten de discusiones aún más. Se conocen solo cuando sea necesario para mayor aclaración de parámetro.

 Al intentar acceder a la propiedad, si se produce ningún error y la propiedad de símbolo se ha asignado un valor, la propiedad "get" devuelve del método `S_OK`. Un valor devuelto de `S_FALSE` indica que la propiedad no es válida para el símbolo actual.

## <a name="in-this-section"></a>En esta sección

[Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)

Describe los diferentes tipos de ubicaciones que puede tener un símbolo.

[Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Describe los tipos de símbolos que forman el léxicas jerarquías como archivos, módulos y funciones.

[Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Describe los tipos de símbolos que corresponden a elementos del lenguaje diferentes, como tipos de valor devuelto de función, matrices y clases.

## <a name="see-also"></a>Vea también

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)