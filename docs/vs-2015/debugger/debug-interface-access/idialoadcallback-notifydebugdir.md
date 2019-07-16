---
title: IDiaLoadCallback::NotifyDebugDir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152007"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Se llama cuando se encontró un directorio de depuración en el archivo .exe.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fExecutable`  
 [in] `TRUE` si el directorio de depuración se lee desde un archivo ejecutable (en lugar de un archivo DBG).  
  
 `cbData`  
 [in] Recuento de bytes de datos en el directorio de depuración.  
  
 `data[]`  
 [in] Una matriz que se rellena con el directorio de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Normalmente, se omite el código de retorno.  
  
## <a name="remarks"></a>Comentarios  
 El [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método invoca esta devolución de llamada cuando encuentra un directorio de depuración al procesar el archivo ejecutable.  
  
 Este método quita la necesidad de información de depuración que no sea la que se encuentra en el archivo .pdb de soporte técnico para el cliente para el archivo ejecutable o depuración de ingeniería inversa. Con estos datos, el cliente puede reconocer el tipo de información de depuración disponible y si se encuentra en el archivo ejecutable o el archivo DBG.  
  
 La mayoría de los clientes no necesitarán esta devolución de llamada porque el `IDiaDataSource::loadDataForExe` método transparente abre los archivos .pdb y .dbg cuando sea necesario atender los símbolos.  
  
## <a name="see-also"></a>Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
