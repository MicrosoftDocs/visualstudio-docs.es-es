---
title: 'Idialoadcallback:: Notifydebugdir | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 006d507a2c77cf2cf3191ce639404ef84b7a7a46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Se llama cuando se encontró un directorio de depuración en el archivo .exe.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fExecutable`  
 [in] `TRUE` si el directorio de depuración se lee desde un archivo ejecutable (en lugar de un archivo .dbg).  
  
 `cbData`  
 [in] Recuento de bytes de datos en el directorio debug.  
  
 `data[]`  
 [in] Una matriz que se rellena con el directorio de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Normalmente se omite el código de retorno.  
  
## <a name="remarks"></a>Comentarios  
 El [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método invoca esta devolución de llamada cuando encuentra un directorio de depuración al procesar el archivo ejecutable.  
  
 Este método quita la necesidad de información de depuración que no sea la que se encuentra en el archivo .pdb de soporte técnico para el cliente para el archivo ejecutable o de depuración de ingeniería inversa. Con estos datos, el cliente puede reconocer el tipo de información de depuración disponible y si se encuentra en el archivo ejecutable o el archivo .dbg.  
  
 La mayoría de los clientes no necesitará esta devolución de llamada porque el `IDiaDataSource::loadDataForExe` método transparente abre los archivos .pdb y .dbg cuando sea necesario atender los símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)