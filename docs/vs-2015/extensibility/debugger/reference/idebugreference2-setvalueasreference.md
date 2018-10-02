---
title: IDebugReference2::SetValueAsReference | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 04a1534064acff7b392c6235c16f1ccf7a38f03e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578902"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugReference2::SetValueAsReference](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugreference2-setvalueasreference).  
  
Establece el valor de una referencia desde otra referencia. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp#  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rgpArgs`  
 [in] Una matriz de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) los objetos utilizados para determinar cómo establecer el valor de referencia.  
  
 `dwArgCount`  
 [in] El número de referencias de la matriz.  
  
 `pValue`  
 [in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto desde el que se va a establecer el valor de propiedad.  
  
 `dwTimeout`  
 [in] Tiempo máximo, en milisegundos para esperar antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

