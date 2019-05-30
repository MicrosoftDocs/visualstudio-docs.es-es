---
title: IDebugSymbolProviderDirect | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ad8bc95e5fe8fa49088d8c1006bc69243dd4977
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320372"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Representa un proveedor de símbolos que se tiene acceso directo a las interfaces de símbolos de metadatos y core.

## <a name="syntax"></a>Sintaxis

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Métodos
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera el identificador de dominio de aplicación dado la dirección de depuración.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera información acerca de los módulos en el grupo de símbolos.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera información sobre el grupo de símbolos de los cuales el proveedor de símbolos es un miembro.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera la información de la importación de metadatos.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera información sobre el método en la dirección de depuración especificado.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera un lector de símbolos de código no administrado.|

## <a name="remarks"></a>Comentarios
 Esta interfaz puede usarse en lugar de la mayoría de las otras interfaces de proveedor de símbolos. Proporciona acceso directo a los metadatos y `CorSym` interfaces.

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll