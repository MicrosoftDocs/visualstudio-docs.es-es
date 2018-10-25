---
title: Idiaframedata | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 933b05bbd9e0ff93a9e132578a72fb44db8be945
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859728"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Realiza el desenredo de pila y devuelve los resultados en una interfaz de marco de recorrido de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `frame`  
 [in] Un [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto que contiene el estado de los registros de marco.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra los posibles valores devueltos para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_DIA_INPROLOG|No se puede ejecutar un marco de pila en el código de prólogo.|  
|E_DIA_SYNTAX|Analizar el error en el programa de marco.|  
|E_DIA_FRAME_ACCESS|No se puede a los registros de acceso o la memoria.|  
|E_DIA_VALUE|Error en el cálculo de un valor (por ejemplo, la división por cero).|  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama durante la depuración para desenredar la pila. El [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto es implementado por la aplicación de cliente para recibir actualizaciones de los registros y para proporcionar los métodos usados por la `execute` método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



