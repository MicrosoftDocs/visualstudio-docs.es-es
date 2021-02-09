---
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29f0e7e3d2fefe0f47dc971ebff273bf2745a5ef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909424"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Representa un proveedor de símbolos que tiene acceso directo a los metadatos y a las interfaces de símbolos principales.

## <a name="syntax"></a>Sintaxis

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Métodos
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera el identificador de dominio de aplicación según la dirección de depuración.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera información sobre los módulos del grupo de símbolos.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera información sobre el grupo de símbolos del que es miembro el proveedor de símbolos.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera la información de importación de metadatos.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera información sobre el método en la dirección de depuración especificada.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera un lector de símbolos para el código no administrado.|

## <a name="remarks"></a>Notas
 Esta interfaz se puede usar en lugar de la mayoría de las demás interfaces de proveedor de símbolos. Proporciona acceso directo a los metadatos e `CorSym` interfaces.

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
