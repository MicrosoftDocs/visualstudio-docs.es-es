---
title: Símbolos y etiquetas de símbolos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 625752125d3c68e9f03afd41cd549995fbc3272e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193536"
---
# <a name="symbols-and-symbol-tags"></a>Símbolos y etiquetas de símbolo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La información de depuración de un programa compilado se almacena en el archivo de base de datos de programa (. pdb) como símbolos a los que se puede tener acceso mediante las API del SDK de Debug interface Access (DIA). Todos los símbolos tienen una propiedad [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) y una propiedad [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) . La `symTag` propiedad indica el tipo de símbolo tal y como se define en la enumeración de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) . La `symIndexId` propiedad es un `DWORD` valor que contiene el identificador único para cada instancia de un símbolo.  
  
 Los símbolos también tienen propiedades que pueden especificar información adicional sobre el símbolo, así como referencias a otros símbolos, a menudo una [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Cuando se consulta una propiedad que contiene una referencia, la referencia se devuelve como un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) . Estas propiedades siempre se emparejan con otra propiedad con el mismo nombre pero con el sufijo "ID", por ejemplo, [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) y [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Las tablas de las [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md), la [jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)y la [jerarquía de clases de los tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) describen las propiedades de cada uno de los distintos tipos de símbolos. Estas propiedades pueden tener información relevante sobre las referencias o a otros símbolos. Dado `*Id` que las propiedades son simplemente identificadores ordinales numéricos de sus propiedades relacionadas, se omiten en discusiones posteriores. Solo se hace referencia a ellos cuando sea necesario para la aclaración de los parámetros.  
  
 Al intentar obtener acceso a la propiedad, si no se produce ningún error y se ha asignado un valor a la propiedad Symbol, el método "Get" de la propiedad devuelve `S_OK` . Un valor devuelto de `S_FALSE` indica que la propiedad no es válida para el símbolo actual.  
  
## <a name="in-this-section"></a>En esta sección  
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)  
 Describe los diferentes tipos de ubicaciones que puede tener un símbolo.  
  
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Describe los tipos de símbolos que forman jerarquías léxicas como archivos, módulos y funciones.  
  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Describe los tipos de símbolos que corresponden a elementos de lenguaje diferentes, como clases, matrices y tipos de valor devueltos de función.  
  
## <a name="see-also"></a>Consulte también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
