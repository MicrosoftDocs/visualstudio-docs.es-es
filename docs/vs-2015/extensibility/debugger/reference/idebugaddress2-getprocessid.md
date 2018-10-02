---
title: IDebugAddress2::GetProcessID | Microsoft Docs
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
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31c935db12a3cbac5bf4e85800e826e1972be4f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577519"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugAddress2::GetProcessID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress2-getprocessid).  
  
Recupera el identificador de proceso que posee el objeto representado por este [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProcID`  
 [out] El identificador de proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)

