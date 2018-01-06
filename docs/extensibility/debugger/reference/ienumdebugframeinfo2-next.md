---
title: IEnumDebugFrameInfo2::Next | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFrameInfo2::Next
helpviewer_keywords: IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee000b2378dacfc5cdac8776404390340897c65d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
Devuelve el siguiente conjunto de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Next(  
   ULONG       celt,  
   FRAMEINFO** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint        celt,  
   FRAMEINFO[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.  
  
 `rgelt`  
 [entrada, salida] Matriz de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) elementos que deben rellenarse.  
  
 `pceltFetched`  
 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si pudieron devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)