---
title: 'IDispatchEx:: GetDispID | Microsoft Docs'
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
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576598"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Asigna un nombre de un solo miembro al DISPID correspondiente, que se puede usar en las llamadas subsiguientes a `IDispatchEx::InvokeEx`.  
  
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
 Se pasó el nombre que se va a asignar.  
  
 `grfdex`  
 Determina las opciones para obtener el identificador de miembro. Puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicita que la búsqueda de nombre se realice de forma que distinga entre mayúsculas y minúsculas. Puede ser omitido por un objeto que no admite la búsqueda que distingue entre mayúsculas y minúsculas.|  
|fdexNameEnsure|Solicita que se cree el miembro si aún no existe. El nuevo miembro debe crearse con el valor `VT_EMPTY`.|  
|fdexNameImplicit|Indica que el llamador está buscando objetos para un miembro de un nombre determinado cuando el objeto base no se especifica explícitamente.|  
|fdexNameCaseInsensitive|Solicita que la búsqueda de nombre se realice de forma que no distinga entre mayúsculas y minúsculas. Puede ser omitido por un objeto que no admite búsquedas sin distinción entre mayúsculas y minúsculas.|  
  
 `pid`  
 Puntero a la ubicación asignada por el llamador para recibir el resultado de DispId. Si se produce un error, `pid` contiene DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`E_OUTOFMEMORY`|Memoria insuficiente.|  
|`DISP_E_UNKNOWNNAME`|No se conocía el nombre.|  
  
## <a name="remarks"></a>Comentarios  
 `GetDispID` se puede utilizar en lugar de `GetIDsOfNames` para obtener el DISPID de un miembro determinado.  
  
 Dado que `IDispatchEx` permite agregar y eliminar miembros, el conjunto de DISPID no permanece constante durante la vigencia de un objeto.  
  
 Se ha quitado el parámetro `riid` sin usar de `IDispatch::GetIDsOfNames`.  
  
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