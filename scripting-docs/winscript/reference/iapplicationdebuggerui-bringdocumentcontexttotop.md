---
title: 'Iapplicationdebuggerui (:: BringDocumentContextToTop | Microsoft Docs'
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
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577810"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Coloca la ventana que contiene el contexto de documento dado en la parte superior de la interfaz de usuario del depurador y desplaza la ventana hasta el contexto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pddc`  
 de Contexto del documento que se va a colocar en la parte superior de la interfaz de usuario del depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_INVALIDARG`|No se conoce el contexto especificado por `pddc`.|  
  
## <a name="remarks"></a>Comentarios  
 Este método coloca la ventana que contiene el contexto de documento dado en la parte superior de la interfaz de usuario del depurador y desplaza la ventana hasta el contexto.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebuggerUI (Interfaz)](../../winscript/reference/iapplicationdebuggerui-interface.md)