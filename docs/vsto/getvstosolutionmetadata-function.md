---
title: "GetVstoSolutionMetadata (funci&#243;n) | Microsoft Docs"
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
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# GetVstoSolutionMetadata (funci&#243;n)
  Este la API la infraestructura de Office y no están diseñados para usarlos directamente en el código.  
  
## Sintaxis  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|No utilice.|  
|*ppSolutionInfo*|No utilice.|  
  
## Valor devuelto  
 Si la función se realiza correctamente, devuelve **S\_OK**.  Si se produce un error en la función, devuelve un código de error.  
  
  