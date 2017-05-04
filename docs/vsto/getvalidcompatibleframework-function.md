---
title: "GetValidCompatibleFramework (funci&#243;n) | Microsoft Docs"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# GetValidCompatibleFramework (funci&#243;n)
  Este la API la infraestructura de Office y no están diseñados para usarlos directamente en el código.  
  
## Sintaxis  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|No utilice.|  
|*pbstrValidFrameworkTag*|No utilice.|  
  
## Valor devuelto  
 Si la función se realiza correctamente, devuelve **S\_OK**.  Si se produce un error en la función, devuelve un código de error.  
  
  