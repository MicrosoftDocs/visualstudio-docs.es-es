---
title: SetWefProcessId (método)
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
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693437"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId (método)
  Proporciona el identificador de proceso que se ejecutará el contenido del marco de trabajo de las extensiones de Web (WEF).  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp  
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
  
  