---
title: "WinRTError (Objeto de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, WinRTError (objeto)"
  - "WinRTError (objeto) [JavaScript]"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WinRTError (Objeto de JavaScript)
Si una llamada a Windows en tiempo de ejecución devuelve un valor HRESULT que indica un error, JavaScript lo convierte en un error especial de Windows en tiempo de ejecución.  Este objeto solo está disponible en aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] \(si Windows en tiempo de ejecución está disponible\) como parte del espacio de nombres global de JavaScript.  
  
## Sintaxis  
  
```  
  
errorObj = new WinRTError();   
```  
  
## Comentarios  
 El tipo de error WinRTError se usa únicamente para errores que se originan en las API de Windows en tiempo de ejecución.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra la forma en que se produce y se detecta un WinRTError.  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## Métodos  
 El objeto WinRTError no tiene métodos.  
  
## Propiedades  
 El objeto WinRTError tiene las mismas propiedades que el objeto [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md).  
  
## Requisitos  
 El objeto WinRTError solo se admite en aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], no en Internet Explorer.  
  
## Vea también  
 [Error \(Objeto\)](../../javascript/reference/error-object-javascript.md)