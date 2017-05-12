---
title: "C&#243;mo: Enviar un correo electr&#243;nico mediante programaci&#243;n"
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
  - "correo electrónico [desarrollo de Office en Visual Studio], enviar"
  - "elementos de correo [desarrollo de Office en Visual Studio], enviar correo electrónico"
  - "Outlook [desarrollo de Office en Visual Studio], crear correo electrónico"
  - "Outlook [desarrollo de Office en Visual Studio], enviar correo electrónico"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Enviar un correo electr&#243;nico mediante programaci&#243;n
  En este ejemplo se envía un mensaje de correo electrónico a contactos que tienen el nombre de dominio **example.com** en sus direcciones de correo electrónico.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ejemplo  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos que tengan el nombre de dominio **example.com** en sus direcciones de correo electrónico.  
  
## Programación eficaz  
 No quite el código del filtro que busca el nombre de dominio **example.com**.  Si quita el filtro, la solución enviará los mensajes de correo electrónico a todos los contactos.  
  
## Vea también  
 [Trabajar con elementos de correo](../vsto/working-with-mail-items.md)   
 [Cómo: Crear un elemento de correo electrónico mediante programación](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Cómo: Obtener acceso a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Cómo: Realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  