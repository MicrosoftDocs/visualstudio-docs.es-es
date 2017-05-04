---
title: "EnsureVSTOComponent (funci&#243;n) | Microsoft Docs"
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
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# EnsureVSTOComponent (funci&#243;n)
  Este la API la infraestructura de Office y no están diseñados para usarlos directamente en el código.  
  
## Sintaxis  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*pProject*|No utilice.|  
  
## Valor devuelto  
 Si la función se realiza correctamente, devuelve **S\_OK**.  Si se produce un error en la función, devuelve un código de error.  
  
  