---
title: "SetWefProcessId (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# SetWefProcessId (M&#233;todo)
  Proporciona el identificador de proceso que se ejecute el contenido web de \(WEF\) de extensiones.  
  
## Sintaxis  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*dwProcessId*|El identificador de proceso que se utilizará para trabajar con el contenido de WEF.|  
  
## Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## Comentarios  
 Se debe llamar a este método una vez creado el proceso de contenido de WEF pero antes de que el contenido de WEF ejecuta.  
  
 Si desea que el entorno de desarrollo para adjuntar un depurador al proceso del contenido de WEF, el entorno debe realizar esta operación en la implementación de este método.  
  
  