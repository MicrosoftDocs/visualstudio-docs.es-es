---
title: IDispatchEx::GetNameSpaceParent | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1abe2a880e12d6a4a3c1dfda32d30722525858f5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154561"
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