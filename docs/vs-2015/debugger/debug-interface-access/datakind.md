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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987086"
---
# <a name="datakind"></a>DataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Indica el ámbito de un valor de datos determinado.  
  
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
