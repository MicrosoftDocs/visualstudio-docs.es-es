---
title: IDebugAddress::GetAddress | Documentos de Microsoft
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
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddb3b6e3d8055dd9a5b6304cf57a355986706b0d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186769"
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

