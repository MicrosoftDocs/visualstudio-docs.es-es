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
ms.openlocfilehash: 8f2b46e420db8addf19ef8694112058bdb8b2f91
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867629"
---
# <a name="datakind"></a>DataKind
Indica el ámbito de un valor de datos determinado.  
  
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
 Elemento de datos es una variable con ámbito de archivo.  
  
 DataIsGlobal  
 Elemento de datos es una variable global.  
  
 DataIsMember  
 Elemento de datos es una variable de miembro de objeto.  
  
 DataIsStaticMember  
 Elemento de datos es una variable estática de la clase.  
  
 DataIsConstant  
 Elemento de datos es un valor constante.  
  
## <a name="remarks"></a>Comentarios  
 Devuelven los valores de esta enumeración la [Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)