---
title: IEnumDebugAddresses::Next | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd662333bb6bc8ac2f7ce04cae0a871fdc6ca661
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190988"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método devuelve el siguiente conjunto de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Next(  
   ULONG           celt,  
   IDebugAddress** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugAddress[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] El número de elementos que se va a recuperar. También especifica el tamaño máximo de la `rgelt` matriz.  
  
 `rgelt`  
 [in, out] Matriz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) elementos que deben rellenarse.  
  
 `pceltFetched`  
 [out] Devuelve el número de elementos realmente devueltos en `rgelt`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si podrían devolverse un menor que el número solicitado de elementos; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)

