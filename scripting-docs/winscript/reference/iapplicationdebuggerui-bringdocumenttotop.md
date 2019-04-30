---
title: IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8a88b44f609113670259492eb82491b16004d29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991125"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Ofrece interfaz de usuario de la ventana que contiene el documento de depuración especificado en la parte superior en el depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddt`  
 [in] Depurar el documento para dar a la parte superior de la interfaz de usuario del depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|No se conoce el documento.|  
  
## <a name="remarks"></a>Comentarios  
 Este método muestra la ventana que contiene el documento de depuración especificado en la parte superior en el depurador de interfaz de usuario.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebuggerUI (Interfaz)](../../winscript/reference/iapplicationdebuggerui-interface.md)