---
title: IDebugProperty2::EnumChildren | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8bd006cd2391acde9743d660b7cf154098e286c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Recupera una lista de los elementos secundarios de la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de indicadores de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica los campos en el enumerado [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructuras son que deben rellenarse.  
  
 `dwRadix`  
 [in] Especifica la base que se usará para dar formato a cualquier información numérica.  
  
 `guidFilter`  
 [in] GUID del filtro utilizado con el `dwAttribFilter` y `pszNameFilter` parámetros para seleccionar qué `DEBUG_PROPERTY_INFO` elementos secundarios son que hay que enumerar. Por ejemplo, `guidFilterLocals` filtros para las variables locales.  
  
 `dwAttribFilter`  
 [in] Una combinación de indicadores de la [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) enumeración que especifica qué tipo de objetos que se va a enumerar, por ejemplo `DBG_ATTRIB_METHOD` para todos los métodos que podrían ser elementos secundarios de esta propiedad. Usar en combinación con la `guidFilter` y `pszNameFilter` parámetros.  
  
 `pszNameFilter`  
 [in] El nombre del filtro utilizado con el `guidFilter` y `dwAttribFilter` parámetros para seleccionar qué `DEBUG_PROPERTY_INFO` elementos secundarios son que hay que enumerar. Por ejemplo, establecer este parámetro en filtros de "MyX" para todos los elementos secundarios con el nombre "MyX."  
  
 `dwTimeout`  
 [in] Especifica el tiempo máximo, en milisegundos, que se esperará antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contiene una lista de las propiedades secundarias.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)