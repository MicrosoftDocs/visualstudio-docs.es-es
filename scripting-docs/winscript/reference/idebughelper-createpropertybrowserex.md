---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
Devuelve un explorador de propiedades que ajuste de VARIANT y tiene en cuenta la conversión personalizada de valores VARIANT o VARTYPE escribe en cadenas.  
  
## Sintaxis  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 \[in\] opóngase que proporciona el formato personalizado para variantes.  
  
 `ppdob`  
 \[out\] explorador de propiedades de El.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método devuelve un explorador de propiedades que ajuste de VARIANT y tiene en cuenta la conversión personalizada de valores VARIANT o VARTYPE escribe en cadenas.  
  
## Vea también  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper \(Interfaz\)](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)