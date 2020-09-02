---
title: 'IDebugReference2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b14ca1293a709dce35f2e8aa45a7fa22bf29845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178189"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 de Matriz de objetos [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que se usa para determinar cómo establecer el valor de referencia.  
  
 `dwArgCount`  
 de Número de referencias de la matriz.  
  
 `pValue`  
 de Objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) a partir del cual se va a establecer el valor de propiedad.  
  
 `dwTimeout`  
 de Tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
