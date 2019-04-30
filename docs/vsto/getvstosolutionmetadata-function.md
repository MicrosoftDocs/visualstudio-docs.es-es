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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796046"
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
