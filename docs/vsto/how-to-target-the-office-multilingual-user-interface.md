---
title: "C&#243;mo: Apuntar a MUI (Multilingual User Interface, Interfaz de usuario multiling&#252;e) de Office | Microsoft Docs"
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
  - "globalización [desarrollo de Office en Visual Studio], apuntar a la interfaz de usuario"
  - "localización [desarrollo de Office en Visual Studio], apuntar a la interfaz de usuario"
  - "MUI [desarrollo de Office en Visual Studio]"
  - "Interfaz de usuario multilingüe [desarrollo de Office en Visual Studio]"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], globalización"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], adaptación"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# C&#243;mo: Apuntar a MUI (Multilingual User Interface, Interfaz de usuario multiling&#252;e) de Office
  MUI \(Multilingual User Interface, Interfaz de usuario multilingüe\) es una característica de Microsoft Office que proporciona al usuario final la posibilidad de cambiar el idioma de la interfaz de usuario.  Por ejemplo, un usuario final que trabaje con una interfaz de usuario en inglés puede cambiar su idioma a español.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si la aplicación la van a usar personas que usan varios idiomas de Office, se puede agregar código para cambiar automáticamente el idioma de las cadenas de la interfaz de usuario de modo que sea compatible con el que utiliza Office en el equipo del usuario \(si éste tiene instalados los recursos correctos\).  
  
### Para comprobar la configuración actual de la interfaz de usuario de Office  
  
1.  Use la propiedad <xref:System.Threading.Thread.CurrentUICulture%2A> del subproceso actual.  Establezca el idioma de las cadenas de la interfaz de usuario de modo que sea compatible con el que usa la versión de Office que se esté ejecutando en el equipo del usuario.  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## Vea también  
 [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)  
  
  