---
title: SetWefProcessId (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dbd5a9ffb2ff9b3833dc8007fdfafb4b1a35857
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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
  
  