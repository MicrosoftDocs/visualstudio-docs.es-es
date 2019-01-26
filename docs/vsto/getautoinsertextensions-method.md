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
ms.openlocfilehash: debe61f07a8aa8711f1bb0b75ff0c2b39a528b21
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875841"
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
