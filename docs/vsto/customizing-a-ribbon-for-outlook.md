---
title: "Personalizar una cinta de opciones para Outlook"
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
  - "Cinta de opciones personalizada, acerca de la personalización de la Cinta de opciones"
  - "personalizar la cinta de opciones, acerca de la personalización de la Cinta de opciones"
  - "Inspectores [desarrollo de Office en Visual Studio]"
  - "Outlook [desarrollo de Office en Visual Studio], cinta de opciones"
  - "Cinta [desarrollo de Office en Visual Studio], Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Personalizar una cinta de opciones para Outlook
  Al personalizar la cinta en Microsoft Office Outlook, debe tener en cuenta dónde aparecerá la cinta personalizada en la aplicación.  Outlook muestra la cinta en la interfaz de usuario \(UI\) de la aplicación principal y en las ventanas que se abren cuando los usuarios realizan ciertas tareas, como crear mensajes de correo electrónico.  Estas ventanas de la aplicación se denominan inspectores.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo: Usar diseñador de la cinta para personalizar la cinta en Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Agregar una Cinta personalizada a la interfaz de usuario de la aplicación principal  
 La interfaz de usuario de la aplicación principal en Outlook se denomina Explorador.  Si está usando el elemento **Cinta \(diseñador visual\)**, puede añadir una cinta al Explorador haciendo clic en la propiedad **RibbonType** de la cinta en la ventana **Propiedades** y seleccionando a continuación **Microsoft.Outlook.Explorer**.  
  
## Asignar una cinta a un Inspector  
 Para identificar el inspector que desea personalizar, debe especificar el tipo de cinta que corresponde a la clase de mensaje del Inspector.  
  
 Si está usando el elemento **Cinta \(diseñador visual\)**, haga clic en la propiedad **RibbonType** de la cinta en la ventana **Propiedades** y, a continuación, seleccione uno o varios de los identificadores de cinta de la lista de valores.  
  
 Puede agregar más de una cinta a un proyecto.  Si más de una cinta comparte el mismo identificador de cinta, reemplace el método CreateRibbonExtensibilityObject de la clase `ThisAddin` de su proyecto para especificar qué cinta se mostrará en tiempo de ejecución.  Para obtener más información, consulte [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  Para obtener más información acerca de cada tipo de cinta, consulte [Personalizar la cinta en Outlook 2007](http://msdn.microsoft.com/es-es/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## Especificar el Tipo de Cinta mediante código XML de Cinta  
 Si está usando el elemento **Cinta \(XML\)**, compruebe el valor del parámetro *ribbonID* en el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> y devuelva la cinta adecuada.  
  
 Visual Studio genera automáticamente el método <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> en el archivo de código de la cinta.  El parámetro *ribbonID* es una cadena que identifica el Explorador o un tipo específico de inspector.  Para ver una lista completa de los posibles valores del parámetro *ribbonID*, consulte [Personalizar la cinta en Outlook 2007](http://msdn.microsoft.com/es-es/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 En el siguiente ejemplo de código se indica cómo mostrar una cinta personalizada únicamente en el inspector `Microsoft.Outlook.Mail.Compose`.  Este es el inspector que se abre cuando un usuario crea un nuevo mensaje de correo electrónico.  La cinta que se debe mostrar se especifica en el método `GetResourceText()`, que se genera en la clase **Ribbon**.  Para obtener más información sobre la clase **Ribbon**, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## Vea también  
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)  
  
  