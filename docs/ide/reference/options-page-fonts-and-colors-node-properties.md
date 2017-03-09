---
title: "P&#225;gina de opciones, Propiedades de nodo Fuentes y colores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Configuración de opciones de herramientas, Propiedades del nodo Fuentes y colores"
  - "automatización [Visual Studio], controlar opciones de herramientas"
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina de opciones, Propiedades de nodo Fuentes y colores
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En este documento se describen las propiedades de fuente y color de una ventana de herramientas que ya está registrada para que aparezca bajo **Fuentes y colores** en la categoría **Entorno** del cuadro de diálogo **Opciones**.  Este método es compatible con la naturaleza dinámica de los grupos de elementos que se pueden colorear, los cuales pueden cambiar si se instalan o desinstalan VSPackages.  
  
 En la sección siguiente se muestra un ejemplo de un tipo de ventana registrada y las propiedades disponibles en cada ventana.  
  
## Editor de texto, impresora o cuadros de diálogos y ventanas de herramientas  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 O bien  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 O bien  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nombre de elemento de propiedad|Valor|Descripción|  
|-------------------------------------|-----------|-----------------|  
|FontFamily|Get\/Set \(String\)|El nombre de fuente que se utilizará, por ejemplo, "Courier New".|  
|FontCharacterSet|Get\/Set \(<xref:EnvDTE.vsFontCharSet>\)|Valor <xref:EnvDTE.vsFontCharSet> que especifica el tipo de juego de caracteres que se utilizará, por ejemplo, hebreo o ruso.|  
|FontSize|Get\/Set \(Short\)|El tamaño de fuente que se utilizará, en puntos.  Por ejemplo, 10 o 12.|  
  
## Vea también  
 [Controlar la configuración de opciones](../Topic/Controlling%20Options%20Settings.md)   
 [Determinar los nombres de los elementos de propiedades en las páginas de opciones](../Topic/Determining%20the%20Names%20of%20Property%20Items%20on%20Options%20Pages.md)   
 [Página de opciones, Propiedades de nodo Entorno](../../ide/reference/options-page-environment-node-properties.md)   
 [Página de opciones, Propiedades de nodo Editor de texto](../../ide/reference/options-page-text-editor-node-properties.md)