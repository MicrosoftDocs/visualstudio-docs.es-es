---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A002A"
  - "vs.message.VB_E_IDWOLENOTRESPONDING"
ms.assetid: 0a4efbb7-72de-43a8-a51a-4a7a24ec743a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft.
La aplicación del servidor no completó la solicitud actual.  
  
 Este error también puede deberse a software antivirus que bloquea algunos procesos de devenv.exe.  Varias características del producto utilizan scripts y el software antivirus podría bloquear estos scripts.  Para obtener información relacionada, vea "PRB: Al iniciar Visual Studio no se abre el IDE" en [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;306905&product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;en-us;306905&product=vsnet).  
  
### Para corregir este error  
  
-   Elija Cambiar a para activar la aplicación e investigar el problema.  
  
     \-O bien\-  
  
     Elija Reintentar para esperar a que la aplicación del servidor termine de procesar la solicitud.  
  
### Para corregir errores relacionados con software antivirus  
  
-   En su software antivirus, especifique que el software debe permitir la ejecución de scripts que se originen desde devenv.exe.  Para ver instrucciones detalladas, consulte la documentación del producto antivirus.