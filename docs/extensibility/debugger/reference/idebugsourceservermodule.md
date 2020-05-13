---
title: IDebugSourceServerModule ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2c362bc4a103c707238acfa3b3148f00c0e25be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719913"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Representa la información del servidor de origen contenida en un archivo PDB.

## <a name="syntax"></a>Sintaxis

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante los motores del depurador y la consume la interfaz de usuario del depurador.

## <a name="methods"></a>Métodos
 En la tabla siguiente `IDebugSourceServerModule`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Recupera una matriz de información del servidor de origen.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
