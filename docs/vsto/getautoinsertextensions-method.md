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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a53148b0130dd05f3ffc3360a518f9b2b66002e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
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
  
  