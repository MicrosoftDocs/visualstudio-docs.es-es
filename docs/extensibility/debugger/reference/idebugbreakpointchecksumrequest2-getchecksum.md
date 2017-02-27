---
title: "IDebugBreakpointChecksumRequest2::GetChecksum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugBreakpointChecksumRequest2::GetChecksum"
ms.assetid: ec434882-e5c0-4d76-a58b-22c260d8626e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBreakpointChecksumRequest2::GetChecksum
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera la suma de comprobación del documento para una solicitud de punto de interrupción según el identificador único del algoritmo de suma de comprobación para utilizar.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetChecksum(   
   REFGUID        guidAlgorithm,  
   CHECKSUM_DATA *pChecksumData  
);  
```  
  
```c#  
public int GetChecksum(   
   ref Guid               guidAlgorithm,  
   out enum_CHECKSUM_DATA pChecksumData  
);  
```  
  
#### Parámetros  
 `guidAlgorithm`  
 \[in\]  Identificador único del algoritmo de suma de comprobación.  
  
 `pChecksumData`  
 \[out\]  Suma de comprobación del documento para la solicitud de punto de interrupción.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
 El ejemplo siguiente se muestra una función que compruebe si coincide con la suma de comprobación de un documento, que está a punto de ser enlazado, uno de la interfaz de usuario.  
  
```cpp#  
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
  
## Vea también  
 [IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)