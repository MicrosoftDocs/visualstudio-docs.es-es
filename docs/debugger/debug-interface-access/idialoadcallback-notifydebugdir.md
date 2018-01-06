---
title: 'Idialoadcallback:: Notifydebugdir | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fad37acafae21c6e82839979360f4ed9574aef1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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