---
title: 'IActiveScriptSiteWindow:: GetWindow | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574352"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Recupera el identificador de una ventana que puede actuar como propietario de una ventana emergente que debe mostrar el motor de scripting.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `phwnd`  
 enuncia Dirección de una variable que recibe el identificador de ventana.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_FAIL` si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 Este método es similar al método `IOleWindow::GetWindow`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)