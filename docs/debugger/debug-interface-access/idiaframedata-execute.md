---
title: 'Idiaframedata:: Execute | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0645d2364712769a6b4f18ef14fbbcb503a51888
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459515"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Realiza el desenredo de la pila y devuelve los resultados en una interfaz de marco de recorrido de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `frame`  
 [in] Un [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto que contiene el estado de los registros de marco.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. La tabla siguiente muestran los posibles valores devueltos para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_DIA_INPROLOG|No se puede ejecutar un marco de pila en el código de prólogo.|  
|E_DIA_SYNTAX|Analizar el error en el programa de marco.|  
|E_DIA_FRAME_ACCESS|No se puede a los registros de acceso o memoria.|  
|E_DIA_VALUE|Error en el cálculo de un valor (por ejemplo, la división por cero).|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método durante la depuración para desenredar la pila. El [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto se implementa mediante la aplicación de cliente para recibir actualizaciones de los registros y para proporcionar métodos usados por la `execute` método.  
  
## <a name="see-also"></a>Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)