---
title: "C&#243;mo: Mover elementos en Outlook mediante programaci&#243;n | Microsoft Docs"
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
  - "carpetas de Outlook [desarrollo de Office en Visual Studio], mover elementos"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Mover elementos en Outlook mediante programaci&#243;n
  En este ejemplo se mueven los mensajes de correo electrónico no leídos desde la **Bandeja de entrada** hacia una carpeta denominada **Prueba**.  En el ejemplo sólo se moverán los mensajes que tengan la palabra **Prueba** en el campo `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## Compilar el código  
 Para este ejemplo se necesita:  
  
-   Una carpeta de correo de Outlook denominada **Prueba**.  
  
-   Un mensaje de correo electrónico que llegue y que tenga la palabra **Prueba** en el campo `Subject`.  
  
## Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Cómo: Recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: Buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Cómo: Realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  