---
title: Idiatable | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ad4b51a125af1f08d8766c4c34a2bdd0c54ff64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582004"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Idiatable](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiatable-item).  
  
Recupera una referencia a la entrada especificada en la tabla.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [Idiatable](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



