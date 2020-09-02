---
title: 'IEnumDebugObjects:: RESET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0874e848c6ae12c4de8168b79633c5402d36e1f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160924"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método restablece la enumeración al primer elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parámetros  
 None  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Después de llamar a este método, la siguiente llamada a [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) devuelve el primer elemento de la enumeración.  
  
## <a name="see-also"></a>Consulte también  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
