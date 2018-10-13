---
title: IDebugIDECallback::DisplayMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98295dea0dd28e7cb87453522214820ccc4f6543
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305765"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Envía la cadena de mensaje especificado a la ventana de salida del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szMessage`  
 [in] Cadena de mensaje que se muestra en la ventana de salida del depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)

