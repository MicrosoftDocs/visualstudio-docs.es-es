---
title: 'IDispatchEx:: GetMemberProperties | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 488f8790ec25532fb611f18e8b24e7e7dba2e2f4
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144556"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Recupera las propiedades de un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `id`  
 Identifica el miembro. Usa `GetDispID` o `GetNextDispID` para obtener el identificador de envío.  
  
 `grfdexFetch`  
 Determina las propiedades que se van a recuperar. Puede ser una combinación de los valores enumerados en `pgrfdex` y/o una combinación de los siguientes valores:  
  
|Value|Significado|  
|-----------|-------------|  
|grfdexPropCanAll|Combina fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct y fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct y fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Combina fdexPropNoSideEffects y fdexPropDynamicType.|  
|grfdexPropAll|Combina grfdexPropCanAll, grfdexPropCannotAll y grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Dirección de un `DWORD` que recibe las propiedades solicitadas. Puede ser una combinación de los siguientes valores:  
  
|Value|Significado|  
|-----------|-------------|  
|fdexPropCanGet|El miembro se puede obtener mediante DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|No se puede obtener el miembro mediante DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|El miembro se puede establecer mediante DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|El miembro no se puede establecer mediante DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|El miembro se puede establecer mediante DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|El miembro no se puede establecer mediante DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|El miembro no tiene efectos secundarios. Por ejemplo, un depurador podría obtener o establecer de forma segura este miembro sin cambiar el estado del script que se está depurando.|  
|fdexPropDynamicType|El miembro es dinámico y puede cambiar durante la vigencia del objeto.|  
|fdexPropCanCall|Se puede llamar al miembro como un método mediante DISPATCH_METHOD.|  
|fdexPropCannotCall|No se puede llamar al miembro como método mediante DISPATCH_METHOD.|  
|fdexPropCanConstruct|Se puede llamar al miembro como un constructor mediante DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|No se puede llamar al miembro como un constructor mediante DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|El miembro puede activar eventos.|  
|fdexPropCannotSourceEvents|El miembro no puede activar eventos.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Value|Significado|
|-|-|  
|`S_OK`|Correcto.|  
|`DISP_E_UNKNOWNNAME`|No se conocía el nombre.|  
  
## <a name="example"></a>Ejemplo  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Consulte también  
 [IDispatchEx (interfaz)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)