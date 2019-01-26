---
title: GetValidCompatibleFramework (función)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 79b97867a3a5c87f1e208d93efacea711ba71efc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869312"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework (función)
  Esta API admite la infraestructura de Office y no está diseñada para utilizarse directamente desde el código.  

## <a name="syntax"></a>Sintaxis  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>Parámetros  

|Parámetro|Descripción|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|No use.|  
|*pbstrValidFrameworkTag*|No use.|  

## <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, devuelve **S_OK**. Si se produce un error en la función, devuelve un código de error.  
