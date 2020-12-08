---
title: Getvstosolutionmetadata (función)
description: Obtenga información sobre cómo la API de Getvstosolutionmetadata (es compatible con la infraestructura de Office y no está diseñada para usarse directamente desde el código.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 205bde9352e2a037b4a08108d8cfce3460034e66
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845042"
---
# <a name="getvstosolutionmetadata-function"></a>Getvstosolutionmetadata (función)
  Esta API es compatible con la infraestructura de Office y no está pensada para usarse directamente desde el código.

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
 Si la función se ejecuta correctamente, devuelve **S_OK**. Si la función presenta un error, devuelve un código de error.
