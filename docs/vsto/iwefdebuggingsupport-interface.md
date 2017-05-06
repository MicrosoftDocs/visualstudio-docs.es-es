---
title: "IWefDebuggingSupport (Interfaz)"
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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# IWefDebuggingSupport (Interfaz)
  Implementado por un entorno de depuración, como Visual Studio, para facilitar la depuración de las aplicaciones de Office.  La aplicación de Office, como word o Excel, obtiene esta interfaz de Visual Studio y después llamar a métodos en la interfaz en determinados puntos durante la sesión de depuración.  
  
## Sintaxis  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## Métodos  
 La tabla siguiente se enumeran los métodos que la interfaz de IWefDebuggingSupport define.  
  
|Name|Descripción|  
|----------|-----------------|  
|[GetAutoInsertExtensions &#40;Método&#41;](../vsto/getautoinsertextensions-method.md)|Obtiene información sobre las aplicaciones de Office que deben automáticamente incrustar durante la depuración.|  
|[SetWefProcessId &#40;Método&#41;](../vsto/setwefprocessid-method.md)|Proporciona el identificador de proceso que se ejecute el contenido web de \(WEF\) de extensiones.|  
  
  