---
title: 'Iapplicationdebugger (:: OnClose | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577874"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
Controla un evento de cierre de la aplicación de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método cuando se llama a `IDebugApplication::Close`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iapplicationdebugger (](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)