---
title: "C&#243;mo: Asociar una p&#225;gina web a una carpeta de Outlook mediante programaci&#243;n"
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
  - "carpetas [desarrollo de Office en Visual Studio], páginas web y"
  - "Outlook [desarrollo de Office en Visual Studio], páginas web adjuntas a carpetas"
  - "páginas web [desarrollo de Office en Visual Studio], carpetas de Outlook"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Asociar una p&#225;gina web a una carpeta de Outlook mediante programaci&#243;n
  En este ejemplo se busca una carpeta denominada `HtmlView` en Microsoft Office Outlook.  Si esta carpeta no existe, el código la crea y le asigna una página web.  Si la carpeta existe, el código muestra el contenido de la carpeta.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Cómo: Recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: Crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  