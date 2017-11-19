---
title: IDispatchEx::GetDispID | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Asigna un nombre de miembro único a su correspondiente identificador DISPID, que, a continuación, se puede usar en las llamadas subsiguientes a `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bstrName`  
 Se pasa en el nombre que debe asignarse.  
  
 `grfdex`  
 Determina las opciones para obtener el identificador de miembro. Esto puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicitudes que se lleva a cabo la búsqueda de nombre de una manera entre mayúsculas y minúsculas. Se puede omitir por objeto que no se admite la búsqueda distingue mayúsculas de minúsculas.|  
|fdexNameEnsure|Solicita que el miembro creará si aún no existe. Se debe crear el nuevo miembro con el valor `VT_EMPTY`.|  
|fdexNameImplicit|Indica que el autor de llamada busca los objetos de un miembro de un nombre determinado cuando no se especifica explícitamente el objeto base.|  
|fdexNameCaseInsensitive|Solicitudes que puede realizar la búsqueda de nombre en mayúsculas y minúsculas. Se puede omitir por objeto que no se admite la búsqueda entre mayúsculas y minúsculas.|  
  
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
 `GetDispID`puede usarse en lugar de `GetIDsOfNames` para obtener el DISPID de un miembro determinado.  
  
 Dado que `IDispatchEx` permite la adición y eliminación de miembros, el conjunto de identificadores DispId no permanezca constante durante la vigencia de un objeto.  
  
 El sin usar `riid` parámetro `IDispatch::GetIDsOfNames` se ha quitado.  
  
## <a name="example"></a>Ejemplo  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (Interfaz)](../../winscript/reference/idispatchex-interface.md)