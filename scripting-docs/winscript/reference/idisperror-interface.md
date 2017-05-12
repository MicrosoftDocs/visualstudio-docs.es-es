---
title: "IDispError (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError (interfaz)"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError (Interfaz)
Proporciona información de error contextual.  
  
> [!NOTE]
>  Esta interfaz no se implementa.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IDispError` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Recupera un tipo determinado de información de error.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Recupera el objeto siguiente de `IDispError` .|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Recupera el código de error del objeto de `IDispError` .|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Devuelve el identificador de programación dependiente del idioma de la clase o la aplicación que activaron el error.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Devuelve la ruta de acceso del archivo de Ayuda y el Id. de contexto del tema que explica el error, si es posible.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Devuelve una descripción del error.|