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
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788701"
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
