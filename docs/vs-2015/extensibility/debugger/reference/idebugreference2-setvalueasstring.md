---
title: IDebugReference2::SetValueAsString | Documentos de Microsoft
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
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aec57f4348f14e972d22ed8644f8eae42713bc25
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757558"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece el valor de una referencia de una cadena. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

