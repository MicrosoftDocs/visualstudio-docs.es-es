---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b26a638c1ac8bd808bae6fa78aaa3cc24dedede5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151959"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recibe las devoluciones de llamada desde el símbolo DIA localizar el procedimiento, lo que permite una interfaz de usuario informar sobre el progreso del intento de ubicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaLoadCallback : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Esta interfaz expone los métodos siguientes:  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Se llama cuando se encontró un directorio de depuración en el archivo .exe.|  
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Se llama cuando se ha abierto un archivo DBG de candidato.|  
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Se llama cuando se ha abierto un archivo .pdb de candidato.|  
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Determina si las consultas del registro pueden usarse para buscar las rutas de búsqueda de símbolos.|  
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Determina si se permite el acceso a un servidor de símbolos para resolver los símbolos.|  
  
## <a name="remarks"></a>Comentarios  
 La aplicación cliente implementa esta interfaz y proporciona una referencia a él en la llamada a la [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
 Para obtener información sobre las restricciones adicionales que se pueden imponer en un proceso de carga, consulte el [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) interfaz.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (SDK de acceso a la interfaz de depuración)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
