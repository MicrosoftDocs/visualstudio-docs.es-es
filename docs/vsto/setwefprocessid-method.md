---
title: SetWefProcessId (método)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3ccce49992073f11245929bf7af0b966537bd079
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886155"
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
