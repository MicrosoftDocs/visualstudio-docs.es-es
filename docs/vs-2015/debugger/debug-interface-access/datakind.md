---
title: DataKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6a72d1093bc8acd9aae788ff357aee2efeb9e52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197635"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica el ámbito determinado de un valor de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum DataKind {   
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
 El elemento de datos es una variable local.  
  
 DataIsStaticLocal  
 El elemento de datos es una variable local estática.  
  
 DataIsParam  
 El elemento de datos es un parámetro formal.  
  
 DataIsObjectPtr  
 El elemento de datos es un puntero de objeto ( `this` ).  
  
 DataIsFileStatic  
 El elemento de datos es una variable de ámbito de archivo.  
  
 DataIsGlobal  
 El elemento de datos es una variable global.  
  
 DataIsMember  
 El elemento de datos es una variable de miembro de objeto.  
  
 DataIsStaticMember  
 El elemento de datos es una variable estática de clase.  
  
 DataIsConstant  
 El elemento de datos es un valor constante.  
  
## <a name="remarks"></a>Comentarios  
 El método [IDiaSymbol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) devuelve los valores de esta enumeración.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
