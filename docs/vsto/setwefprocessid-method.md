---
title: SetWefProcessId (método)
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
ms.openlocfilehash: 1352ccc9318061be4a2f9ad2da7d63715acd6721
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978361"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId (método)
  Proporciona el identificador de proceso que se ejecutará el contenido del marco de trabajo de extensiones de Web (WEF).

## <a name="syntax"></a>Sintaxis

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwProcessId*|El identificador de proceso que se usará para ejecutar el contenido de WCF.|

## <a name="return-value"></a>Valor devuelto
 Un valor HRESULT que indica si el método se ha completado correctamente.

## <a name="remarks"></a>Comentarios
 Este método debe llamarse una vez creado el proceso de contenido de WEF pero antes de que se ejecuta cualquier contenido de WCF.

 Si desea que el entorno de desarrollo para adjuntar a un depurador al proceso de contenido de WCF, el entorno debe realizar esta operación en la implementación de este método.
