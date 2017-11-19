---
title: IDispatchEx::GetMemberProperties | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Recupera las propiedades de un miembro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 Determina qué propiedades que se recuperarán. Esto puede ser una combinación de los valores enumerados en `pgrfdex` o una combinación de los siguientes valores:  
  
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
|fdexPropNoSideEffects|El miembro no tiene efectos secundarios. Por ejemplo, un depurador podría sin ningún riesgo get/set/llamada a este miembro sin cambiar el estado de la secuencia de comandos que se está depurando.|  
|fdexPropDynamicType|El miembro es dinámico y puede cambiar durante la vigencia del objeto.|  
|fdexPropCanCall|El miembro se puede llamar como un método utilizando DISPATCH_METHOD.|  
|fdexPropCannotCall|El miembro no se puede llamar como un método utilizando DISPATCH_METHOD.|  
|fdexPropCanConstruct|El miembro puede llamarse como un constructor con DISPATCH_CONSTRUCT.|  
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
  
```  
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