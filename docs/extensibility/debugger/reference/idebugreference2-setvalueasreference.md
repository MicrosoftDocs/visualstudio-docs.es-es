---
title: IDebugReference2::SetValueAsReference | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::SetValueAsReference
helpviewer_keywords: IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7b684f540bf5488f1febc93228c73259ccf03c77
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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