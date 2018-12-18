---
title: IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs
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
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6a9ca8db857caddf3b35ea8d0b03bae7bab273b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773696"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera la cadena del valor de una métrica de evaluador de expresión dada su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetEEMetricString(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetEEMetricString(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidLang`  
 [in] Identificador único del lenguaje de programación.  
  
 `guidVendor`  
 [in] Identificador único del proveedor.  
  
 `pszMetric`  
 [in] Nombre de la métrica.  
  
 `pbstrValue`  
 [out] Devuelve la cadena del valor de métrica.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

