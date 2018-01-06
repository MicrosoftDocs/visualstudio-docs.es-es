---
title: IDebugProperty2::GetPropertyInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetPropertyInfo
helpviewer_keywords: IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 094ad1d47aa3c1af3ad24020a1caac6ddc6a665d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
Obtiene el [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructura que describe una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de valores de la [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) enumeración que especifica los campos que se debe rellenarse el `pPropertyInfo` estructura.  
  
 `nRadix`  
 [in] Base que se usará para dar formato a cualquier información numérica.  
  
 `dwTimeout`  
 [in] Especifica el tiempo máximo, en milisegundos, que se esperará antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
 `rgpArgs`  
 [entrada, salida] Reservado para uso futuro; establecer en un valor null.  
  
 `dwArgCount`  
 [in] Reservado para uso futuro; establecer en cero.  
  
 `pPropertyInfo`  
 [out] A [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estructura que se rellena con la descripción de la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)