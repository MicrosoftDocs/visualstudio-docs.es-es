---
title: IDebugReference2::GetReferenceInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a40211c49f5255dba608d38529f7c56ac990e671
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120454"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Obtiene el [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura que describe una referencia. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de indicadores de la [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) enumeración que determina los campos que se rellene el [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura.  
  
 `nRadix`  
 [in] La base que se usará para dar formato a cualquier información numérica.  
  
 `dwTimeout`  
 [in] Tiempo máximo, en milisegundos, que se esperará antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
 `rgpArgs`  
 [in] Una matriz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objetos. Reservado para uso futuro; establecer en un valor null.  
  
 `dwArgCount`  
 [in] El número de argumentos de referencia en la `rgpArgs` matriz. Reservado para uso futuro; se establece en 0.  
  
 `pReferenceInfo`  
 [out] A [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura que se rellena con una descripción de la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)