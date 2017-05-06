---
title: "IManagedAddin::Load"
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
helpviewer_keywords: 
  - "IManagedAddin::Load"
  - "Load (método)"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  Se llama a este elemento cuando se carga un complemento VSTO administrado.  
  
## Sintaxis  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|*bstrManifestURL*|Ruta de acceso del manifiesto del complemento VSTO.|  
|*pdispApplication*|Un puntero a un IDispatch que representa la aplicación host que está cargando el complemento VSTO.|  
  
## Valor devuelto  
 Un valor HRESULT que indica si el método se ha completado correctamente.  
  
## Comentarios  
 Un manifiesto es un archivo \(normalmente un archivo XML\) que proporciona información que se usa para cargar el complemento VSTO. Por ejemplo, un manifiesto puede especificar la ubicación del ensamblado del complemento VSTO y la clase de punto de entrada, para así poder crear una instancia cuando se carga el complemento VSTO.  
  
 El parámetro *bstrManifestURL* contiene el valor de la entrada `Manifest` que se encuentra en la clave de registro HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nombre de la aplicación\>*\\Addins\\*\<identificador del complemento\>* del complemento VSTO. Para obtener más información, consulta [Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md).  
  
 Implemente el método [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) para realizar tareas como configurar el dominio de la aplicación y la directiva de seguridad del complemento VSTO que se va a cargar.  
  
## Vea también  
 [Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  