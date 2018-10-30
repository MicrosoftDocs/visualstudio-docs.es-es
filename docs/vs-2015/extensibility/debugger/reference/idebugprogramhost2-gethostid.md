---
title: IDebugProgramHost2::GetHostId | Microsoft Docs
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
- IDebugProgramHost2::GetHostId
helpviewer_keywords:
- IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf22a112b94850290ef29ce72e9353520461cb23
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894097"
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtiene el identificador de proceso del proceso que hospeda este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```csharp  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwId`  
 [in, out] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estructura que se rellena con la información del identificador de proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)

