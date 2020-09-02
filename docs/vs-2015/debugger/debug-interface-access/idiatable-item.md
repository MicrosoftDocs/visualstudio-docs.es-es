---
title: IDiaTable::Item | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574806"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 de Índice de la entrada de tabla en el intervalo comprendido entre 0 y `count` -1, donde `count` es devuelto por el método [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 enuncia Devuelve un `IUnknown` objeto que representa la entrada de la tabla especificada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una tabla representa una colección de objetos. Dependiendo de estos objetos, el parámetro de elemento se puede convertir en la interfaz adecuada. Por ejemplo, si una tabla contiene objetos [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , el parámetro Element se puede convertir a la `IDiaSegment` interfaz.  
  
 Es un enfoque más común llamar al `QueryInterface` método en la interfaz [IDiaTable](../../debugger/debug-interface-access/idiatable.md) para la interfaz del enumerador adecuada y usar los métodos específicos del enumerador para tener acceso al contenido de la tabla. Vea la interfaz [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) para obtener un ejemplo.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
