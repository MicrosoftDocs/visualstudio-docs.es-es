---
title: IApplicationDebuggerUI::BringDocumentContextToTop | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fab017ab286957cf2c4be35832b1db877b339bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Abre la ventana que contiene el contexto del documento especificado a la parte superior de la interfaz de usuario del depurador y se desplaza la ventana para el contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddc`  
 [in] Contexto del documento para llevar a la parte superior de la interfaz de usuario del depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|El contexto especificado por `pddc` no se conoce.|  
  
## <a name="remarks"></a>Comentarios  
 Este método pone la ventana que contiene el contexto del documento especificado a la parte superior de la interfaz de usuario del depurador y desplaza la ventana para el contexto.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebuggerUI (Interfaz)](../../winscript/reference/iapplicationdebuggerui-interface.md)