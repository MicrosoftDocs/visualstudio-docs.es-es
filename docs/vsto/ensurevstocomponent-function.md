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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a04cfc249efa4640df2b2e4b1c5f4b43ed52ace2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846121"
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
