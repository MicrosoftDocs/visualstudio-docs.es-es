---
title: IDebugProgramPublisher2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721526"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Esta interfaz permite que un motor de depuración (DE) o proveedores de puertos personalizados registren programas para la depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Visual Studio implementa esta interfaz para registrar los programas que se están depurando con el fin de hacerlos visibles para la depuración en varios procesos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
Llame a `CoCreateInstance` la `CLSID_ProgramPublisher` función de COM para obtener esta interfaz (consulte el ejemplo). Un DE o un proveedor de puertos personalizado utiliza esta interfaz para registrar nodos de programa que representan programas que se están depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Hace que un nodo de programa esté disponible para los DE y el administrador de depuración de sesión (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Quita un nodo de programa para que ya no esté disponible.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Pone un programa a disposición de los ES y el SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Elimina un programa para que ya no esté disponible.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Establece una marca que indica que hay un depurador presente.|

## <a name="remarks"></a>Observaciones
Esta interfaz hace que los programas y nodos de programa estén disponibles (es decir, los "publica") para su uso por los DE y el administrador de depuración de sesión (SDM). Para tener acceso a los programas publicados y nodos de programa, utilice el [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaz. Esta es la única manera en que Visual Studio puede reconocer que se está depurando un programa.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg.h

Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo crear instancias del publicador del programa y registrar un nodo de programa. Esto se toma del Tutorial, [Publicación del nodo de programa](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
