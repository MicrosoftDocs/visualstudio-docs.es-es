---
title: IDebugProgramDestroyEventFlags2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722505"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Permite que un motor de depuración invalide el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario al finalizar una sesión de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante motores de depuración. Es útil para hosts que pueden crear y destruir varios programas a lo largo de la duración de un proceso.

## <a name="methods"></a>Métodos
 En la tabla siguiente `IDebugProgramDestroyEventFlags2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera las marcas de destrucción del programa.|

## <a name="remarks"></a>Observaciones
 El comportamiento predeterminado [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de la interfaz de usuario es volver al modo de diseño después de que todos los programas hayan enviado un evento de destrucción de programa. Esta interfaz permite que un motor de depuración cambie ese comportamiento.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
