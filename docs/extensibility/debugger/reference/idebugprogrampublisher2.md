---
description: Esta interfaz permite a un motor de depuración (DE) o a proveedores de puertos personalizados registrar programas para la depuración.
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c51fac369ed91f00c91482dd7069362d758b7346
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065104"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Esta interfaz permite a un motor de depuración (DE) o a proveedores de puertos personalizados registrar programas para la depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
Visual Studio implementa esta interfaz para registrar los programas que se están depurando con el fin de hacerlos visibles para la depuración en varios procesos.

## <a name="notes-for-callers"></a>Notas para llamadores
Llame `CoCreateInstance` a la función de com con `CLSID_ProgramPublisher` para obtener esta interfaz (vea el ejemplo). Un o un proveedor DE puerto personalizado usa esta interfaz para registrar los nodos de programa que representan los programas que se están depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Hace que un nodo de programa esté disponible para DEs y el administrador de depuración de sesión (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Quita un nodo de programa para que ya no esté disponible.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Hace que un programa esté disponible para DEs y el SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Quita un programa para que ya no esté disponible.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Establece una marca que indica que hay un depurador presente.|

## <a name="remarks"></a>Observaciones
Esta interfaz permite que los programas y los nodos de programas estén disponibles (es decir, "los publica") para su uso por parte de DEs y el administrador de depuración de sesión (SDM). Para tener acceso a los programas y los nodos de programa publicados, use la interfaz [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Esta es la única manera en que Visual Studio puede reconocer que se está depurando un programa.

## <a name="requirements"></a>Requisitos
Encabezado: msdbg. h

Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo crear una instancia del publicador de programa y registrar un nodo de programa. Esto se toma del tutorial, [publicar el nodo del programa](/previous-versions/bb161795(v=vs.90)).

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

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
