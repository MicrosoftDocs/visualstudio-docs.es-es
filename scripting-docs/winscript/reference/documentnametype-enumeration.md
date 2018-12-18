---
title: Enumeración DOCUMENTNAMETYPE | Documentos de Microsoft
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
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640585"
---
# <a name="documentnametype-enumeration"></a>Enumeración DOCUMENTNAMETYPE
Describe qué tipo se va a obtener para un documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|DOCUMENTNAMETYPE_APPNODE|Obtiene el nombre tal y como aparece en el árbol de la aplicación.|  
|DOCUMENTNAMETYPE_TITLE|Obtiene el nombre tal y como aparece en la barra de título del Visor.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Obtiene el nombre de archivo sin una ruta de acceso.|  
|DOCUMENTNAMETYPE_URL|Obtiene la dirección URL del documento.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Obtiene el título que se anexa a la enumeración para la identificación.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)