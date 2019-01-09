---
title: IDispatchEx::GetMemberProperties | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 51e01ef3fa6d5e0611875f6402b79e53f8c83cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088197"
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
 Determina qué propiedades se deben recuperar. Esto puede ser una combinación de los valores enumerados en `pgrfdex` o una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|grfdexPropCanAll|Combina fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct y fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct y fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Combina fdexPropNoSideEffects y fdexPropDynamicType.|  
|grfdexPropAll|Combina grfdexPropCanAll, grfdexPropCannotAll y grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Dirección de un `DWORD` que recibe las propiedades solicitadas. Esto puede ser una combinación de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexPropCanGet|El miembro puede obtenerse mediante DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|El miembro no se puede obtener mediante DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|El miembro puede establecerse utilizando DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|El miembro no se puede establecer mediante DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|El miembro puede establecerse utilizando DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|El miembro no se puede establecer mediante DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|El miembro no tiene efectos secundarios. Por ejemplo, un depurador puede con seguridad get/set/llamada este miembro sin cambiar el estado de la secuencia de comandos que se está depurando.|  
|fdexPropDynamicType|El miembro es dinámico y puede cambiar durante la vigencia del objeto.|  
|fdexPropCanCall|El miembro se puede llamar a un método mediante DISPATCH_METHOD.|  
|fdexPropCannotCall|No se puede llamar al miembro como un método mediante DISPATCH_METHOD.|  
|fdexPropCanConstruct|El miembro se puede llamar a un constructor con DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|No se puede llamar al miembro como un constructor con DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|El miembro puede desencadenar eventos.|  
|fdexPropCannotSourceEvents|El miembro no puede desencadenar eventos.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|||  
|-|-|  
|`S_OK`|Correcto.|  
|`DISP_E_UNKNOWNNAME`|No se conoce el nombre.|  
  
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
  
## <a name="see-also"></a>Vea también  
 [IDispatchEx (interfaz)](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)