---
title: Método Setwefprocessid (
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
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537337"
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

## <a name="remarks"></a>Observaciones
 Se debe llamar a este método después de crear el proceso de contenido de WEF, pero antes de que se ejecute cualquier contenido de WEF.

 Si desea que el entorno de desarrollo asocie un depurador al proceso de contenido de WEF, el entorno debe realizar esta operación en la implementación de este método.
