---
title: "Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. Please include a description of the work you’re doing in Visual Studio and when possible instruction | Microsoft Docs"
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
  - "vs.message.VB_E_IDWOLEBUSY"
  - "vs.message.0x800A002B"
ms.assetid: 688fdf7e-c3ef-41f1-bc22-9f88f8f5b353
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Visual Studio is waiting for an operation to complete. If you regularly encounter this delay during normal usage please report this problem to Microsoft. Please include a description of the work you’re doing in Visual Studio and when possible instruction
La aplicación del servidor está ocupada y no puede completar la solicitud actual.  
  
 Este error también puede deberse a software antivirus que bloquea algunos procesos de devenv.exe.  Varias características del producto utilizan scripts y el software antivirus podría bloquear estos scripts.  Para obtener información relacionada, vea "PRB: Al iniciar Visual Studio no se abre el IDE" en [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;306905&product\=vsnet](http://support.microsoft.com/default.aspx?scid=kb;en-us;306905&product=vsnet).  
  
### Para corregir errores relacionados con aplicaciones del servidor  
  
1.  Elija Cambiar a para activar la aplicación e investigar el problema.  
  
     \-O bien\-  
  
     Elija Reintentar para esperar a que la aplicación del servidor termine de procesar la solicitud.  
  
     \-O bien\-  
  
     Elija Cancelar para terminar la solicitud.  
  
### Para corregir errores relacionados con software antivirus  
  
-   En su software antivirus, especifique que el software debe permitir la ejecución de scripts que se originen desde devenv.exe.  Para ver instrucciones detalladas, consulte la documentación del producto antivirus.