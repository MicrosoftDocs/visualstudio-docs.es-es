---
title: "GetAutoInsertExtensions (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d222f7b6751381ceb4ebdb27bb6a6bf223616df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions (Método)
  Obtiene información sobre las aplicaciones de Office que se van a insertar automáticamente durante la depuración.  
  
 Este método está reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*psaExtensionNames*|Los nombres de extensión de las aplicaciones de Office.|  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 Cada aplicación para Office que se va a insertar se devuelve como un nombre de extensión de aplicación de Office, que se corresponde con un valor bajo HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. El host debe buscar estos valores en el registro y, a continuación, insertar automáticamente las extensiones.  
  
  