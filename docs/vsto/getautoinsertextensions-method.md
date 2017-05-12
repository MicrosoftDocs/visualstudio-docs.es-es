---
title: "GetAutoInsertExtensions (M&#233;todo)"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetAutoInsertExtensions (M&#233;todo)
  Obtiene información sobre las aplicaciones de Office que deben automáticamente incrustar durante la depuración.  
  
 Este método está reservado para un uso futuro.  
  
## Sintaxis  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*psaExtensionNames*|Los nombres de la extensión de las aplicaciones de Office.|  
  
## Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## Comentarios  
 Cada aplicación de Office se inserte se devuelve como nombre de la extensión de la aplicación de Office, que corresponde a un valor HKEY\_CURRENT\_USER ent dict AnyPathTillLastSlash \\ el software \\ Microsoft Office \\ \\ WEF \\ desarrollador.  El host debe buscar estos valores en el registro y después automáticamente insertar las extensiones.  
  
  