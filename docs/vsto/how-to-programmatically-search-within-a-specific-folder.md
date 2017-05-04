---
title: "C&#243;mo: Buscar en una carpeta espec&#237;fica mediante programaci&#243;n | Microsoft Docs"
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
  - "carpetas de Outlook [desarrollo de Office en Visual Studio], buscar"
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# C&#243;mo: Buscar en una carpeta espec&#237;fica mediante programaci&#243;n
  En este ejemplo de código se utilizan los métodos `Find` y `FindNext` para buscar texto en el campo Asunto de mensajes de correo electrónico que se encuentren en la **Bandeja de entrada**.  Este método utiliza un filtro de cadena para comprobar la letra T como la letra inicial del texto del `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_OL_SearchFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchFolder/CS/thisaddin.cs#1)]  
  
## Vea también  
 [Trabajar con carpetas](../vsto/working-with-folders.md)   
 [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)   
 [Cómo: Recuperar una carpeta por su nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  