---
title: 'Idiatable:: Item | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: af10c9924bb7b319c34b017812289ead48929b13
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
 [in] El índice de la entrada de tabla en el intervalo de 0 a `count`-1, donde `count` devuelto por la [idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)método.  
  
 `element`  
 [out] Devuelve un `IUnknown` objeto que representa la entrada de la tabla especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una tabla representa una colección de objetos. En función de los objetos, el parámetro de elemento puede convertirse a la interfaz adecuada. Por ejemplo, si una tabla contiene [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos, a continuación, se puede convertir el parámetro de elemento en el `IDiaSegment` interfaz.  
  
 Es un enfoque más común para llamar a la `QueryInterface` método en el [IDiaTable](../../debugger/debug-interface-access/idiatable.md) de interfaz para la interfaz de enumerador correspondiente y usar métodos específicos del enumerador para tener acceso al contenido de la tabla. Consulte la [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interfaz para obtener un ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)