---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197558"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Realiza el desenredo de la pila y devuelve los resultados en una interfaz de marco de recorrido de pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `frame`  
 de Un objeto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) que contiene el estado de los registros de fotogramas.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran los posibles valores devueltos para este método.  
  
|Value|Descripción|  
|-----------|-----------------|  
|E_DIA_INPROLOG|No se puede ejecutar un marco de pila en código de prólogo.|  
|E_DIA_SYNTAX|Error de análisis detectado en el programa de marco.|  
|E_DIA_FRAME_ACCESS|No se puede obtener acceso a los registros o a la memoria.|  
|E_DIA_VALUE|Error en el cálculo de un valor (por ejemplo, división por cero).|  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método durante la depuración para desenredar la pila. El objeto [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) se implementa mediante la aplicación cliente para recibir actualizaciones de los registros y para proporcionar métodos utilizados por el `execute` método.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
