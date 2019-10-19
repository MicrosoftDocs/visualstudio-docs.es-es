---
title: IDispatchEx::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576621"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Elimina un miembro por su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bstrName`  
 Nombre del miembro que se va a eliminar.  
  
 `grfdex`  
 Determina si el nombre del miembro distingue mayúsculas de minúsculas. Puede ser uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicita que la búsqueda de nombre se realice de forma que distinga entre mayúsculas y minúsculas. Un objeto que no admite búsquedas con distinción de mayúsculas y minúsculas puede omitir.|  
|fdexNameCaseInsensitive|Solicita que la búsqueda de nombre se realice de forma que no distinga entre mayúsculas y minúsculas. Un objeto que no admite búsquedas sin distinción de mayúsculas y minúsculas puede omitir.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`S_FALSE`|El miembro existe pero no se puede eliminar.|  
  
## <a name="remarks"></a>Comentarios  
 Si se elimina el miembro, el DISPID debe permanecer válido para `GetNextDispID`.  
  
 Si se elimina un miembro con un nombre determinado y posteriormente se vuelve a crear un miembro con el mismo nombre, el DISPID debe ser el mismo. (Si los miembros que difieren solo en mayúsculas y minúsculas son el "mismo" depende del objeto).  
  
## <a name="example"></a>Ejemplo  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)