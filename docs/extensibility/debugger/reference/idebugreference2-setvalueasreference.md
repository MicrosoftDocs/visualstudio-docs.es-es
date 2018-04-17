---
title: IDebugReference2::SetValueAsReference | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0ce62358df758b7f4cf3ef0883cf0ac457aaf1f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Establece el valor de una referencia desde otra referencia. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rgpArgs`  
 [in] Una matriz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objetos que se usan para determinar cómo establecer el valor de referencia.  
  
 `dwArgCount`  
 [in] El número de referencias de la matriz.  
  
 `pValue`  
 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto desde el que se establecerá el valor de propiedad.  
  
 `dwTimeout`  
 [in] Tiempo máximo, en milisegundos, que se esperará antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)