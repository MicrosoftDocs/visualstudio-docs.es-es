---
title: Ensurevstocomponent (función)
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
ms.openlocfilehash: cf55fc6669edd33d1b8896ee85f33ab2c04e844f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543590"
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
