---
title: Idiatable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e8ba825c0dba1b0218e53f9ad66f6958602d0c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953984"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Recupera una referencia a la entrada especificada en la tabla.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `index`  
 [in] El índice de la entrada de tabla en el intervalo de 0 a `count`-1, donde `count` devuelto por la [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)método.  
  
 `element`  
 [out] Devuelve un `IUnknown` objeto que representa la entrada de la tabla especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una tabla representa una colección de objetos. En función de esos objetos, se puede convertir el parámetro de elemento en la interfaz adecuada. Por ejemplo, si una tabla contiene [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos, a continuación, se puede convertir el parámetro de elemento en el `IDiaSegment` interfaz.  
  
 Es un enfoque más común para llamar a la `QueryInterface` método en el [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaz para la interfaz de enumerador correspondiente y use métodos específicos del enumerador para tener acceso al contenido de la tabla. Consulte la [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaz para obtener un ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)