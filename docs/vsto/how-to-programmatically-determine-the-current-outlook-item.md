---
title: "C&#243;mo: Determinar el elemento actual de Outlook mediante programaci&#243;n"
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
  - "correo electrónico [desarrollo de Office en Visual Studio], elemento actual"
  - "elementos de correo [desarrollo de Office en Visual Studio], actuales"
  - "Outlook [desarrollo de Office en Visual Studio], elemento actual"
  - "SelectionChange (evento)"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# C&#243;mo: Determinar el elemento actual de Outlook mediante programaci&#243;n
  En este ejemplo se utiliza el evento Explorer.SelectionChange para mostrar el nombre de la carpeta actual y alguna información sobre el elemento seleccionado.  El código muestra a continuación el elemento seleccionado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## Compilar el código  
 Para este ejemplo se necesita:  
  
-   Una cita, un contacto y elementos de correo electrónico de Microsoft Office Outlook.  
  
## Vea también  
 [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)   
 [Cómo: Recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: Buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  