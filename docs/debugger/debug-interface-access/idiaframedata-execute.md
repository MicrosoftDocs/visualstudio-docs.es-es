---
title: 'Idiaframedata:: Execute | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8ad08fd9800fdc197d4218fa55c83487e132f25d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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