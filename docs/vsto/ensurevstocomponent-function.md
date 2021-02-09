---
title: Ensurevstocomponent (función)
description: Obtenga información sobre cómo la API de Ensurevstocomponent (es compatible con la infraestructura de Office y no está diseñada para usarse directamente desde el código.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17f52a469d93a843ef776c125e15a37db22277e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910477"
---
# <a name="ensurevstocomponent-function"></a>Ensurevstocomponent (función)
  Esta API es compatible con la infraestructura de Office y no está pensada para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pProject*|No use.|

## <a name="return-value"></a>Valor devuelto
 Si la función se ejecuta correctamente, devuelve **S_OK**. Si la función presenta un error, devuelve un código de error.
