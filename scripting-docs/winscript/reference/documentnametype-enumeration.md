---
title: DOCUMENTNAMETYPE (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094775"
---
# <a name="documentnametype-enumeration"></a>Enumeración DOCUMENTNAMETYPE
Describe qué tipo se va a obtener para un documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Descripción|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Obtiene el nombre tal como aparece en el árbol de la aplicación.|  
|DOCUMENTNAMETYPE_TITLE|Obtiene el nombre tal como aparece en la barra de título del Visor.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Obtiene el nombre de archivo sin una ruta de acceso.|  
|DOCUMENTNAMETYPE_URL|Obtiene la dirección URL del documento.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Obtiene el título que se anexa con enumeración para la identificación.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)