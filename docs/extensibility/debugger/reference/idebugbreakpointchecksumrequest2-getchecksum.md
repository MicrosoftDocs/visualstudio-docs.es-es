---
description: Recupera la suma de comprobación del documento para una solicitud de punto de interrupción dado el identificador único del algoritmo de suma de comprobación que se va a usar.
title: 'IDebugBreakpointChecksumRequest2:: getChecksum (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2::GetChecksum
ms.assetid: ec434882-e5c0-4d76-a58b-22c260d8626e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5661a2753e022ae3907092efd7aab9a046107df5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143433"
---
# <a name="idebugbreakpointchecksumrequest2getchecksum"></a>IDebugBreakpointChecksumRequest2::GetChecksum
Recupera la suma de comprobación del documento para una solicitud de punto de interrupción dado el identificador único del algoritmo de suma de comprobación que se va a usar.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetChecksum(
    REFGUID        guidAlgorithm,
    CHECKSUM_DATA *pChecksumData
);
```

```csharp
public int GetChecksum(
    ref Guid               guidAlgorithm,
    out enum_CHECKSUM_DATA pChecksumData
);
```

## <a name="parameters"></a>Parámetros
`guidAlgorithm`\
de Identificador único del algoritmo de suma de comprobación.

`pChecksumData`\
enuncia Suma de comprobación de documento para la solicitud de punto de interrupción.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una función que comprueba si la suma de comprobación de un documento, que está a punto de enlazarse, coincide con una de la interfaz de usuario.

```cpp
bool CDebugProgram::DoChecksumsMatch(CDebugPendingBreakpoint *pPending, CDebugCodeContext *pContext)
{
    bool fRet = false;
    HRESULT hRes;

    // Get the checksum for the document we are about to bind to from the pdb side
    GUID guidAlgorithmId;
    BYTE *pChecksum = NULL;
    ULONG cNumBytes = 0;

    hRes = pContext->GetDocumentChecksumAndAlgorithmId(&guidAlgorithmId, &pChecksum, &cNumBytes);

    if ( S_OK == hRes )
    {
        // Get checksum data for the document from the UI (request) side
        CComPtr<IDebugBreakpointChecksumRequest2> pChecksumRequest;

        hRes = pPending->GetChecksumRequest(&pChecksumRequest);

        if ( S_OK == hRes )
        {
            CHECKSUM_DATA data;

            hRes = pChecksumRequest->GetChecksum(guidAlgorithmId, &data);

            if ( S_OK == hRes )
            {
                if ( data.ByteCount == cNumBytes && memcmp(data.pBytes, pChecksum, cNumBytes) == 0 )
                    fRet = true;
                else
                    fRet = false;

                // Free up data allocated for checksum data
                CoTaskMemFree(data.pBytes);
            }
            else
                fRet = true; // checksums not available - user disabed checksums
        }
        else
            fRet = true; // we couldn't get checksum from UI - default to past behavior

        // free up space allocated for checksum from pdb
        CoTaskMemFree(pChecksum);
    }
    else
        fRet = true; // we don't have a checksum to compare with.

    return ( fRet );
}
```

## <a name="see-also"></a>Consulte también
- [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)
