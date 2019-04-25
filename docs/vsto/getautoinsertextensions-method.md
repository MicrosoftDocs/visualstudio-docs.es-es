---
title: GetAutoInsertExtensions (método)
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
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611183"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions (método)
  Obtiene información acerca de las aplicaciones de Office que se insertarán automáticamente durante la depuración.

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
|*psaExtensionNames*|Los nombres de extensión de las aplicaciones de Office.|

## <a name="return-value"></a>Valor devuelto
 Un valor HRESULT que indica si el método se ha completado correctamente.

## <a name="remarks"></a>Comentarios
 Cada aplicación de Office va a insertar se devuelve como un nombre de extensión de aplicación de Office, que corresponde a un valor bajo **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. El host debe buscar estos valores en el registro y, a continuación, insertar automáticamente las extensiones.
