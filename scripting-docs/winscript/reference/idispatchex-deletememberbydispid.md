---
title: IDispatchEx::D eleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144641"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Elimina un miembro por DispId.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 Identificador del miembro. Usa `GetDispID` o `GetNextDispID` para obtener el identificador de envío.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Value|Significado|
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|El miembro existe pero no se puede eliminar.|  
  
## <a name="remarks"></a>Observaciones  
 Si se elimina el miembro, el DISPID debe seguir siendo válido para `GetNextDispID` .  
  
 Si se elimina un miembro con un nombre determinado y posteriormente se vuelve a crear un miembro con el mismo nombre, el DISPID debe ser el mismo. (Si los nombres de miembro que difieren solo en mayúsculas y minúsculas son el "mismo" depende del objeto).  
  
## <a name="example"></a>Ejemplo  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDispatchEx (interfaz)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)