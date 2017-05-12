---
title: "IDebugHelper::CreatePropertyBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowser"
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowser
Devuelve un explorador de propiedades que ajuste de VARIANT.  
  
## Sintaxis  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### Parámetros  
 `pvar`  
 \[in\] variante de la raíz a examinar.  
  
 `bstrName`  
 \[in\] nombre de la raíz.  
  
 `pdat`  
 \[in\] subproceso en el que se va a solicitar propiedades.  Si este parámetro es NULL, no se realiza el ningún cálculo de referencias.  
  
 `ppdob`  
 \[out\] explorador de propiedades de El.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve un explorador de propiedades que ajuste de VARIANT.  
  
## Vea también  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper \(Interfaz\)](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)