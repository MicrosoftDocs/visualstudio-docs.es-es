---
title: DOCUMENTNAMETYPE (enumeración) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955225"
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