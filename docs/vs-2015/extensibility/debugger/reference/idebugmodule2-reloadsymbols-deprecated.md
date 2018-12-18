---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
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
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20a3d7715e3dacac1e7e64e5d52434e48615e7e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757885"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

OBSOLETO. NO USE. Vuelve a cargar los símbolos para este módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszUrlToSymbols`  
 [in] La ruta de acceso al almacén de símbolos.  
  
 `pbstrDebugMessage`  
 [out] Devuelve un mensaje informativo, como un mensaje de error o estado, que se muestra a la derecha del nombre del módulo en la ventana módulos.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Siempre debe devolver un motor de depuración `E_FAIL`.  
  
## <a name="remarks"></a>Comentarios  
 Este método ya no se admite. Implemente el [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) método en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

