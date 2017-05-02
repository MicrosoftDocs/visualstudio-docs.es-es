---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
Devuelve el identificador de programación dependiente del idioma de la clase o la aplicación que activaron el error.  
  
## Sintaxis  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### Parámetros  
 `pbstrSource`  
 \[out\] vinculadas que contiene un identificador de programación, en el formulario `progname.objectname`.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método se utiliza para determinar la clase o la aplicación donde se ha producido la excepción.  El identificador de programación se puede devolver en el lenguaje especificado por el identificador. de configuración regional \(LCID\) proporcionado en el momento de la invocación.  
  
> [!NOTE]
>  Este método no está implementado.  
  
## Vea también  
 [IDispError \(Interfaz\)](../../winscript/reference/idisperror-interface.md)