---
title: 'IEnumDebugObjects:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6333c9474ea2bb40f4327d2ebdd7595722cf1b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180472"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método omite el número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   [In] uint celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de elementos que se van a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el final y `S_FALSE` se devuelve.  
  
## <a name="see-also"></a>Consulte también  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
