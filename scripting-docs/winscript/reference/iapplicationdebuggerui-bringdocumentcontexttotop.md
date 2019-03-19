---
title: IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 596f9357a8553bf6c39140a6948d8ae3085c3210
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147688"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Pone la ventana que contiene el contexto del documento especificado en la parte superior de la interfaz de usuario del depurador y se desplaza a la ventana para el contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddc`  
 [in] Contexto de documento para dar a la parte superior de la interfaz de usuario del depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|El contexto especificado por `pddc` no se conoce.|  
  
## <a name="remarks"></a>Comentarios  
 Este método pone la ventana que contiene el contexto del documento especificado en la parte superior de la interfaz de usuario del depurador y desplaza a la ventana para el contexto.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebuggerUI (Interfaz)](../../winscript/reference/iapplicationdebuggerui-interface.md)