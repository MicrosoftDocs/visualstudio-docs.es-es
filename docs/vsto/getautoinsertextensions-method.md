---
title: Método Getautoinsertextensions (
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
ms.openlocfilehash: 24fd5768a9eafa4a023aeabf21c862ea1a0d1891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931531"
---
# <a name="getautoinsertextensions-method"></a>Método Getautoinsertextensions (
  Obtiene información sobre las aplicaciones de Office que se insertarán automáticamente durante la depuración.

 Este método está reservado para un uso futuro.

## <a name="syntax"></a>Sintaxis

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*psaExtensionNames*|Los nombres de extensión de las aplicaciones para Office.|

## <a name="return-value"></a>Valor devuelto
 Un valor HRESULT que indica si el método se ha completado correctamente.

## <a name="remarks"></a>Notas
 Cada aplicación de Office que se va a insertar se devuelve como un nombre de extensión de aplicación de Office, que corresponde a un valor en **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. El host debe buscar estos valores en el registro y, a continuación, insertar automáticamente las extensiones.
