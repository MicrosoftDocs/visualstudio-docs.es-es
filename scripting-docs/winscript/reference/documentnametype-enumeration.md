---
title: "DOCUMENTNAMETYPE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DOCUMENTNAMETYPE (enumeración)"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DOCUMENTNAMETYPE (Enumeraci&#243;n)
Describe qué tipo para recopilar para un documento.  
  
## Sintaxis  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## Members  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|DOCUMENTNAMETYPE\_APPNODE|Obtiene el nombre que aparece en el árbol de la aplicación.|  
|DOCUMENTNAMETYPE\_TITLE|Obtiene el nombre que aparece en la barra de título del visor.|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|Obtiene el nombre de archivo sin una ruta.|  
|DOCUMENTNAMETYPE\_URL|Obtiene la dirección URL del documento.|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|Obtiene el título anexado a la enumeración para su identificación.|  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)