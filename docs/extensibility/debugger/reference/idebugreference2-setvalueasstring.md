---
title: IDebugReference2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86fcc0e73248c766e6fa8b4db7fd3456250055ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952722"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Establece el valor de una referencia de una cadena. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszValue`  
 [in] El valor como una cadena.  
  
 `dwRadix`  
 [in] La base que se usará para dar formato a cualquier información numérica.  
  
 `dwTimeout`  
 [in] Tiempo máximo, en milisegundos para esperar antes de volver de este método. Use `INFINITE` para esperar indefinidamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)