---
title: IDebugThread2::GetThreadProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetThreadProperties
helpviewer_keywords:
- IDebugThread2::GetThreadProperties
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41164b906ba3fca25347aaa65031b4dd5befe48
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449845"
---
# <a name="idebugthread2getthreadproperties"></a>IDebugThread2::GetThreadProperties
Obtiene las propiedades que describen este subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetThreadProperties (
    THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES*     ptp
);
```

```csharp
int GetThreadProperties (
    enum_THREADPROPERTY_FIELDS dwFields,
    THREADPROPERTIES[]         ptp
);
```

#### <a name="parameters"></a>Parámetros
`dwFields`  
[in] Una combinación de marcas de la [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) enumeración que determina qué campos de `ptp` deben rellenarse.

`ptp`  
[in, out] Un [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) estructura que se rellena con las propiedades del subproceso.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Normalmente, se muestra la información devuelta por este método en el **subprocesos** ventana de depuración.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para una sencilla `CProgram` objeto que implementa el [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interfaz.

```cpp
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,
                                      THREADPROPERTIES *ptp)
{
    HRESULT hr = E_FAIL;

    // Check for valid argument.
    if (ptp)
    {
        // Create an array of buffers at ptp the size of the
        // THREADPROPERTIES structure and set all of the
        // buffers at ptp to 0.
        memset(ptp, 0, sizeof (THREADPROPERTIES));

        // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.
        if (dwFields & TPF_ID)
        {
            // Check for successful assignment of the current thread ID to
            // the dwThreadId of the passed THREADPROPERTIES.
            if (GetThreadId(&(ptp->dwThreadId)) == S_OK)
            {
                // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator
                // of the passed THREADPROPERTIES.
                ptp->dwFields |= TPF_ID;
            }
        }

        hr = S_OK;
    }
    else
        hr = E_INVALIDARG;

    return hr;
}
```

## <a name="see-also"></a>Vea también
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)  
[THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)  
[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
