---
title: IDebugSourceServerModule | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5210b819d78bcec1cac5179ac679cf201279e9fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Representa la información del servidor de origen que se encuentra en un archivo PDB.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante motores de depuración y utilizada por la interfaz de usuario del depurador.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugSourceServerModule`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matriz de información del servidor de origen.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll