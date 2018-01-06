---
title: "SetWefProcessId (método) | Documentos de Microsoft"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dd4abab178c951c6150653a1228c2077c5585808
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="setwefprocessid-method"></a>SetWefProcessId (Método)
  Proporciona el identificador de proceso que se ejecutará el contenido del marco de trabajo de las extensiones de Web (WEF).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*dwProcessId*|El identificador de proceso que se usará para ejecutar el contenido WEF.|  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## <a name="remarks"></a>Comentarios  
 Este método debe llamarse una vez creado el proceso de contenido WEF pero antes de ejecuta cualquier contenido WEF.  
  
 Si desea que el entorno de desarrollo para adjuntar a un depurador al proceso contenido WEF, el entorno debe realizar esta operación en la implementación de este método.  
  
  