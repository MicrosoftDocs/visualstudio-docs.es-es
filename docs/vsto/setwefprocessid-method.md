---
title: Método Setwefprocessid (
description: Obtenga información sobre cómo el método Setwefprocessid (proporciona el identificador de proceso que ejecutará el contenido del marco de extensiones web (WEF).
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
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882413"
---
# <a name="setwefprocessid-method"></a>Método Setwefprocessid (
  Proporciona el identificador de proceso que ejecutará el contenido del marco de extensiones web (WEF).

## <a name="syntax"></a>Sintaxis

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwProcessId*|El identificador de proceso que se usará para ejecutar el contenido de WEF.|

## <a name="return-value"></a>Valor devuelto
 Un valor HRESULT que indica si el método se ha completado correctamente.

## <a name="remarks"></a>Notas
 Se debe llamar a este método después de crear el proceso de contenido de WEF, pero antes de que se ejecute cualquier contenido de WEF.

 Si desea que el entorno de desarrollo asocie un depurador al proceso de contenido de WEF, el entorno debe realizar esta operación en la implementación de este método.
