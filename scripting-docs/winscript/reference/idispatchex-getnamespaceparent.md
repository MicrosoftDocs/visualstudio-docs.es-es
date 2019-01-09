---
title: IDispatchEx::GetNameSpaceParent | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 142248d4cfedb2d63025fc873c5574c163fcafd4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087508"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Recupera la interfaz para el elemento de espacio de nombres primario de un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppunk`  
 Dirección de un `IUnknown` puntero de interfaz que recibe la interfaz del espacio de nombres primario.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si es correcto o un código de error definido por OLE en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)