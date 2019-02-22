---
title: GetVstoSolutionMetadata (función)
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
ms.openlocfilehash: d7714e78e897e6c8b391a6c30e9a548671ce80c4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635012"
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
