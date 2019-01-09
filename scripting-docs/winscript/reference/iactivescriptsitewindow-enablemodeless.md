---
title: IActiveScriptSiteWindow::EnableModeless | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cea23890539ca80abf8e3e58b0f8c48b7ca1fc9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093020"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Hace que el host habilitar o deshabilitar su ventana principal, así como los cuadros de diálogo no modal.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fEnable`  
 [in] Marca que, si `TRUE`, permite que la ventana principal y los cuadros de diálogo no modales o, si `FALSE`, las deshabilita.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_FAIL` si se produjo un error.  
  
## <a name="remarks"></a>Comentarios  
 Este método es idéntico a la `IOleInPlaceFrame::EnableModeless` método.  
  
 Se pueden anidar las llamadas a este método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)