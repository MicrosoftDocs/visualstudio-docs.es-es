---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732316"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Esta interfaz proporciona varios métodos para tener acceso a los servicios de notificación y el servidor de un puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para representar el puerto de depuración para tener acceso a los programas. Un proveedor de Puerto personalizado también puede implementar esta interfaz si controla la depuración remota.

## <a name="notes-for-callers"></a>Notas para llamadores
 Un argumento de los métodos de la interfaz [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) proporciona esta interfaz. La llamada a [QueryInterface](/cpp/atl/queryinterface) en una interfaz [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) también puede obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Además de los métodos definidos en [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtiene la interfaz de notificación de puerto desde este puerto.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtiene la interfaz para el servidor que hospeda este puerto.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina si este puerto se está ejecutando en el equipo local.|

## <a name="remarks"></a>Observaciones
 El nombre " `IDebugDefaultPort2` " es un bit de un nombre poco apropiado, ya que no representa un puerto predeterminado. Podría denominarse "IDebugPort3".

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
