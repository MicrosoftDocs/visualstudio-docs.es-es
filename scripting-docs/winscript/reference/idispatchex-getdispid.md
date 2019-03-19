---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95ab1d72e5b2f608c51ac6e56be1986df8945ec2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152868"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Asigna un nombre de miembro único a su correspondiente identificador DISPID, que, a continuación, se puede usar en las llamadas subsiguientes a `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bstrName`  
 Pasa el nombre que debe asignarse.  
  
 `grfdex`  
 Determina las opciones para obtener el identificador de miembro. Esto puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicitudes que se realiza la búsqueda de nombre en minúsculas. Puede omitir el objeto que no es compatible con la búsqueda distingue mayúsculas de minúsculas.|  
|fdexNameEnsure|Solicita que el miembro se crean si aún no existe. Se debe crear el nuevo miembro con el valor `VT_EMPTY`.|  
|fdexNameImplicit|Indica que el llamador está buscando objetos miembro de un nombre determinado cuando no se especifica explícitamente el objeto base.|  
|fdexNameCaseInsensitive|Solicitudes que se realiza la búsqueda de nombre en mayúsculas y minúsculas. Puede omitir el objeto que no es compatible con la búsqueda de mayúsculas y minúsculas.|  
  
 `pid`  
 Puntero a la ubicación asignada por el llamador para recibir el resultado DISPID. Si se produce un error, `pid` contiene DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`E_OUTOFMEMORY`|Memoria insuficiente.|  
|`DISP_E_UNKNOWNNAME`|No se conoce el nombre.|  
  
## <a name="remarks"></a>Comentarios  
 `GetDispID` puede usarse en lugar de `GetIDsOfNames` para obtener el DISPID de un miembro determinado.  
  
 Dado que `IDispatchEx` permite la adición y eliminación de miembros, el conjunto de identificadores DispId no permanezca constante durante la vigencia de un objeto.  
  
 Los no usados `riid` parámetro `IDispatch::GetIDsOfNames` se ha quitado.  
  
## <a name="example"></a>Ejemplo  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)