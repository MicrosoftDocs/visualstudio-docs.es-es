---
title: Idebugapplication (::D ebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d52acf0e4b32f0ced63b53a6b37ffe62f1d948e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575018"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
Hace que la cadena especificada se muestre en el entorno de desarrollo integrado (IDE) del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstr`  
 de Cadena que se va a mostrar en el depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método permite a un motor de lenguaje implementar la compatibilidad con la salida de depuración específica del lenguaje. Normalmente, la cadena se muestra en la ventana de salida del depurador.  
  
 Este método hace que se llame a `IApplicationDebugger::onDebugOutput`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplication (](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)