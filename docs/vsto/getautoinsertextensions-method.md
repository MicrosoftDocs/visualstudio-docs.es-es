---
title: Método Getautoinsertextensions (
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
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543512"
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

## <a name="remarks"></a>Comentarios
 Cada aplicación de Office que se va a insertar se devuelve como un nombre de extensión de aplicación de Office, que corresponde a un valor en **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**. El host debe buscar estos valores en el registro y, a continuación, insertar automáticamente las extensiones.
