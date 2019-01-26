---
title: IDebugSettingsCallback2::GetMetricDword | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricDword
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb4331dec219e31c3e0151ebc3475ebbf5c99a04
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988225"
---
# <a name="idebugsettingscallback2getmetricdword"></a>IDebugSettingsCallback2::GetMetricDword
Recupera el valor de una métrica dado su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMetricDword(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetMetricDword(  
   string   pszType,  
   ref Guid guidSection,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszType`  
 [in] Tipo de la métrica.  
  
 `guidSection`  
 [in] Identificador único de la sección.  
  
 `pszMetric`  
 [in] Nombre de la métrica.  
  
 `pdwValue`  
 [out] Devuelve el valor de la métrica.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)