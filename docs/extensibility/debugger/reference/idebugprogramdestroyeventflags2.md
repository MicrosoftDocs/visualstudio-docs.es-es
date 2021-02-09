---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd43b93f8a74e0e1fcb12ac9be4da47142a79519
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848226"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permite que un motor de depuración invalide el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario al finalizar una sesión de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementan los motores de depuración. Resulta útil para los hosts que pueden crear y destruir varios programas a lo largo de la duración de un proceso.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugProgramDestroyEventFlags2` .

|Método|Descripción|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera las marcas de destrucción del programa.|

## <a name="remarks"></a>Notas
 El comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario es volver al modo de diseño después de que todos los programas hayan enviado un evento de destrucción de programas. Esta interfaz permite a un motor de depuración cambiar ese comportamiento.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
