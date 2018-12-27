---
title: GetAutoInsertExtensions (método)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a12adf6e83e58b877e36dd65d98b617cda3a39b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647215"
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
  
  