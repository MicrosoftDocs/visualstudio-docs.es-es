---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998407"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve una estructura que describe un objeto y su ubicación dentro de su ámbito o el contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in, out] Un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que se rellena mediante este método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura se pasa a este método, que, a continuación, se rellena con la información adecuada. Cómo se interpreta esta información depende del tipo de información que se devuelve como el propio controlador de símbolos. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
