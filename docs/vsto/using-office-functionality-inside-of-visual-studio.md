---
title: "Usar la funcionalidad de Office dentro de Visual Studio | Microsoft Docs"
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
  - "aplicaciones de Office [desarrollo de Office en Visual Studio]"
  - "funcionalidad de Office dentro de Visual Studio"
  - "seguridad [desarrollo de Office en Visual Studio], protección de documentos"
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Usar la funcionalidad de Office dentro de Visual Studio
  Al crear un proyecto de nivel de documento, el documento y la aplicación asociada se hospedan dentro de Visual Studio para que pueda diseñar y trabajar directamente con el documento.  Una aplicación de Microsoft Office abierta en Visual Studio, generalmente funciona de la forma esperada.  Sin embargo, algunas funcionalidades de la aplicación son diferentes o inaccesibles.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Protección de documentos  
 Microsoft Office Word y Microsoft Office Excel incluyen características de protección de documentos que se pueden usar en los proyectos.  Sin embargo, si la protección de documentos está habilitada mientras el documento está abierto en Visual Studio, puede que le impida realizar algunas modificaciones del diseño.  Para obtener más información, vea [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md).  
  
## Information Rights Management  
 Information Rights Management \(IRM\) está disponible en Microsoft Office Word y en Microsoft Office Excel.  IRM puede ayudarle a impedir que las personas no autorizadas vean o modifiquen información confidencial.  No obstante, IRM también puede impedir que el código se ejecute.  Para obtener más información, vea [Información general sobre la administración de permisos sobre la información y las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## Protección mediante contraseña  
 Los documentos de Microsoft Office Word y los libros de Microsoft Office Excel se pueden configurar de manera que no puedan abrirlos las personas que no conozcan la contraseña.  La protección mediante contraseña se administra de manera diferente en Word y en Excel, y puede influir en el proceso de desarrollo.  Para obtener más información, vea [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md).  
  
## Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Información general sobre la administración de permisos sobre la información y las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: Abrir soluciones de Office sin ejecutar código](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  