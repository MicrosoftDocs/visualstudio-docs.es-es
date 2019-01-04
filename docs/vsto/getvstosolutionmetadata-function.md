---
title: GetVstoSolutionMetadata (función)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0cb0acd57ff04b7487d5311f8a05219b3ce0c0a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853728"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata (función)
  Esta API admite la infraestructura de Office y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|No use.|  
|*ppSolutionInfo*|No use.|  
  
## <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, devuelve **S_OK**. Si se produce un error en la función, devuelve un código de error.  
