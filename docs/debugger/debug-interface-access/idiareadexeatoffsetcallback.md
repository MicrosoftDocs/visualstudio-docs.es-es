---
title: IDiaReadExeAtOffsetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e27e63a4a76e188ebf078b3101f7259f62dbefe
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042730"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Permite que una aplicación cliente proporcionar los bytes de un archivo ejecutable como especificado por la posición del archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaReadExeAtOffsetCallback`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Lee el número especificado de bytes a partir del desplazamiento especificado desde un archivo ejecutable.|  
  
## <a name="remarks"></a>Comentarios  
 La aplicación cliente implementa esta interfaz para proporcionar los bytes del archivo ejecutable con un desplazamiento absoluto en el archivo del ejecutable. Para utilizar una dirección virtual relativa, implementar el [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Este método es implementada por la aplicación cliente y pasa a la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método como un método alternativo para leer el archivo.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (SDK de acceso a la interfaz de depuración)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)