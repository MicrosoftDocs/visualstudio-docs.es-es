---
title: IDebugModule2::ReloadSymbols_Deprecated | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModule2::ReloadSymbols
helpviewer_keywords: IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3923431ed4936cf34a077d8d5d818c96e9630221
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETO. NO UTILICE. Vuelve a cargar los símbolos para este módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Siempre debe devolver un motor de depuración `E_FAIL`.  
  
## <a name="remarks"></a>Comentarios  
 Ya no se admite este método. Implemente el [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) método en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)