---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
Este error aparece cuando intenta crear un nuevo archivo desde la ventana Comandos, pero incluye caracteres no compatibles en el nombre de archivo.  
  
 Los nombres de archivo no pueden contener los caracteres siguientes:  
  
-   signo de número \(\#\)  
  
-   porcentaje \(%\)  
  
-   símbolo de Y comercial \(&\)  
  
-   asterisco \(\*\)  
  
-   barra vertical \(&#124;\)  
  
-   barra diagonal inversa \(\\\)  
  
-   dos puntos \(:\)  
  
-   signo de comillas \("\)  
  
-   menor que \(\<\)  
  
-   mayor que \(\>\)  
  
-   punto \(.\)  
  
-   signo de interrogación \(?\)  
  
-   barra diagonal \(\/\)  
  
-   espacios iniciales o finales \(' '\)  
  
-   nombres reservados para Windows o DOS \(nul, aux, con, com1, lpt1, etc.\)  
  
### Para corregir este error  
  
-   Escriba el comando con un nuevo nombre de archivo que no contenga los caracteres mostrados anteriormente.  
  
## Vea también  
 [Nuevo archivo \(Comando\)](../ide/reference/new-file-command.md)   
 [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md)