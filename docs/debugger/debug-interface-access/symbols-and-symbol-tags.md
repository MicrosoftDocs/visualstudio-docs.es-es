---
title: "Símbolos y etiquetas de símbolo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c3e51d02171455cd5b0b6051ed3b05c6d95278ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="symbols-and-symbol-tags"></a>Símbolos y etiquetas de símbolo
Información de depuración acerca de un programa compilado se almacena en el archivo de programa (.pdb) de la base de datos como símbolos que sean accesibles mediante la API del SDK de Debug Interface Access (DIA). Todos los símbolos tienen un [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) y un [idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) propiedad. El `symTag` propiedad indica el tipo de símbolo definido por el [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración. El `symIndexId` propiedad es una `DWORD` valor que contiene el identificador único para cada instancia de un símbolo.  
  
 Símbolos también tienen propiedades que pueden especificar información adicional acerca de los símbolos, así como las referencias a otros símbolos con mayor frecuencia una [idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) o [idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Al consultar una propiedad que contiene una referencia, la referencia se devuelve como un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto. Estas propiedades son siempre emparejadas con otra propiedad con el mismo nombre pero sufijo con "Id", por ejemplo, [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) y [idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Las tablas de [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md), [jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), y [jerarquía de tipos de símbolos de clase](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) describir las propiedades para cada uno de los diferentes tipos de símbolos. Estas propiedades pueden tener información relevante sobre o referencias a otros símbolos. Dado que la `*Id` propiedades son identificadores ordinal simplemente numéricos de sus propiedades relacionadas, se omiten de aún más las discusiones. Se conocen sólo cuando sea necesario para una aclaración de parámetro.  
  
 Al intentar obtener acceso a la propiedad, si se produce ningún error y la propiedad de símbolo se ha asignado un valor, la propiedad "get" método devuelve `S_OK`. Un valor devuelto de `S_FALSE` indica que la propiedad no es válida para el símbolo actual.  
  
## <a name="in-this-section"></a>En esta sección  
 [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)  
 Describe los diferentes tipos de ubicaciones que puede tener un símbolo.  
  
 [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Describe los tipos de símbolos que forman jerarquías léxicas como archivos, módulos y funciones.  
  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Describe los tipos de símbolos que corresponden a elementos del lenguaje diferentes, como tipos de valor devuelto de función, matrices y clases.  
  
## <a name="see-also"></a>Vea también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)