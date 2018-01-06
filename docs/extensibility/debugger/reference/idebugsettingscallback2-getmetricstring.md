---
title: IDebugSettingsCallback2::GetMetricString | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9827e20b70631f65090fbd5e965cf7ac1d5f882
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
Recupera la cadena del valor de la métrica de acuerdo con su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszType`  
 [in] Tipo de la métrica.  
  
 `guidSection`  
 [in] Identificador único de la sección.  
  
 `pszMetric`  
 [in] Nombre de la métrica.  
  
 `pbstrValue`  
 [out] Devuelve la cadena del valor de la métrica.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)