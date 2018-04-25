---
title: DataKind | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c3de9ef6128c3cd5ca6eae80a257b3dc2982cd0f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="datakind"></a>DataKind
Indica el ámbito determinado de un valor de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## <a name="elements"></a>Elementos  
 DataIsUnknown  
 No se puede determinar el símbolo de datos.  
  
 DataIsLocal  
 Elemento de datos es una variable local.  
  
 DataIsStaticLocal  
 Elemento de datos es una variable local estática.  
  
 DataIsParam  
 Elemento de datos es un parámetro formal.  
  
 DataIsObjectPtr  
 Elemento de datos es un puntero de objeto (`this`).  
  
 DataIsFileStatic  
 Elemento de datos es una variable de ámbito de archivo.  
  
 DataIsGlobal  
 Elemento de datos es una variable global.  
  
 DataIsMember  
 Elemento de datos es una variable de miembro de objeto.  
  
 DataIsStaticMember  
 Elemento de datos es una variable estática de la clase.  
  
 DataIsConstant  
 Elemento de datos es un valor constante.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración son devueltos por la [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)