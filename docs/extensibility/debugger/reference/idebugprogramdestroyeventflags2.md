---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1b131679a287fb555fcf2a78a803c77457d47ca
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343509"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permite que un motor de depuración invalidar el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] al finalizar una sesión de depuración de interfaz de usuario.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante motores de depuración. Es útil para los hosts que pueden crear y destruir varios programas durante la vigencia de un proceso.

## <a name="methods"></a>Métodos
 La tabla siguiente muestran los métodos de `IDebugProgramDestroyEventFlags2`.

|Método|Descripción|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera el programa destruir marcas.|

## <a name="remarks"></a>Comentarios
 El comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] es la interfaz de usuario volver al modo de diseño después de que todos los programas han enviado un programa de evento de destrucción. Esta interfaz permite que un motor de depuración cambiar este comportamiento.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll