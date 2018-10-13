---
title: IDebugDocumentChecksum2::GetChecksumAndAlgorithmId | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentChecksum2::GetChecksumAndAlgorithmI
- GetChecksumAndAlgorithmI
ms.assetid: 25efef99-0ef3-4332-a752-607605fc6e67
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f20342c6cf1db9cb06466a6d51ea97d303ccdbab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221616"
---
# <a name="idebugdocumentchecksum2getchecksumandalgorithmid"></a>IDebugDocumentChecksum2::GetChecksumAndAlgorithmId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera el identificador de suma de comprobación y el algoritmo de documento dado el número máximo de bytes que se utilizará.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetChecksumAndAlgorithmId(   
   GUID  *pRetVal,  
   ULONG cMaxBytes,  
   BYTE  *pChecksum,  
   ULONG *pcNumBytes  
);  
```  
  
```csharp  
public int GetChecksumAndAlgorithmId(   
   out Guid pRetVal,  
   uint     cMaxBytes,  
   out byte pChecksum,  
   out uint pcNumBytes  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRetVal`  
 [out] Identificador único para el algoritmo de suma de comprobación.  
  
 `cMaxBytes`  
 [in] Número máximo de bytes que se usará para la suma de comprobación.  
  
 `pChecksum`  
 [out] Valor de la suma de comprobación.  
  
 `pcNumBytes`  
 [out] Número real de bytes utilizados por la suma de comprobación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente usa este método para obtener la suma de comprobación y el algoritmo para un documento.  
  
```cpp#  
HRESULT CDebugCodeContext::GetDocumentChecksumAndAlgorithmId(GUID *pguidAlgorithm, BYTE **ppChecksum, ULONG *pcNumBytes)  
{  
    HRESULT hRes = E_FAIL;  
  
    *ppChecksum = NULL;  
    *pcNumBytes = 0;  
  
    CComPtr<IDebugDocumentContext2> pDocContext;  
  
    hRes = this->GetDocumentContext(&pDocContext);  
  
    if ( HREVAL(S_OK, hRes) )  
    {  
        CComQIPtr<IDebugDocumentChecksum2> pDocChecksum(pDocContext);  
  
        if ( pDocChecksum != NULL )  
        {  
            // Figure out the size of the checksum buffer required  
            ULONG cNumBytes = 0;  
  
            hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, 0, NULL, &cNumBytes);  
  
            if ( S_OK == hRes )  
            {  
                // check to see if we got back valid values  
                if ( cNumBytes && GUID_NULL != (*pguidAlgorithm) )  
                {  
                    // Alloc space for the checksum data  
                    BYTE *pChecksum = (BYTE*) CoTaskMemAlloc(cNumBytes);  
  
                    if ( pChecksum )  
                    {  
                        // Get the buffer containing the checksum info  
                        hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, cNumBytes, pChecksum, &cNumBytes);  
  
                        if ( HREVAL(S_OK, hRes) )  
                        {  
                            *ppChecksum = pChecksum;  
                            *pcNumBytes = cNumBytes;  
                        }  
                        else  
                        {  
                            CoTaskMemFree(pChecksum);  
                        }  
                    }  
                    else  
                        hRes = E_OUTOFMEMORY;  
                }  
                else  
                    hRes = S_FALSE; // lang doesn't support checksums  
            }  
            else  
                hRes = S_FALSE; // failed to work out checksum info  
        }  
        else  
            hRes = S_FALSE; // SH doesn't support checksums  
    }  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)

