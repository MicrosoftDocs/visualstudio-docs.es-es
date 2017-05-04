---
title: "Protecci&#243;n mediante contrase&#241;a en documentos de Office | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], permisos restringidos"
  - "documentos de Office [desarrollo de Office en Visual Studio], permisos restringidos"
  - "contraseñas [desarrollo de Office en Visual Studio], protecciones de documentos"
  - "permisos [desarrollo de Office en Visual Studio]"
  - "libros [desarrollo de Office en Visual Studio], permisos restringidos"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Protecci&#243;n mediante contrase&#241;a en documentos de Office
  Existe la posibilidad de establecer una contraseña para los documentos de Microsoft Office Word y los libros de Microsoft Office Excel de manera que quienes no conozcan dicha contraseña no puedan abrirlos.  Esta opción se denomina **Contraseña al abrir**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede crear proyectos de nivel de documento utilizando documentos y libros existentes que tengan habilitada la opción **Contraseña al abrir**.  El comportamiento en Visual Studio es distinto para los documentos de Word y Excel que tienen habilitada la opción **Contraseña al abrir**.  
  
 Para obtener más información sobre cómo habilitar la opción **Contraseña de apertura**, consulte la Ayuda de Word o de Excel.  
  
## Comportamiento de Excel y Word  
 Cada vez que abra en Visual Studio un libro de Excel que tenga habilitada la opción **Contraseña al abrir**, Excel le pedirá que escriba la contraseña.  Cuando compile la solución, se le pedirá que vuelva a escribir la contraseña, porque el documento se abre durante la compilación.  
  
 La primera vez que abra en Visual Studio un documento de Word que tenga habilitada la opción **Contraseña al abrir**, Word le pedirá que la escriba.  Una vez escrita la contraseña correcta, se quitará del documento la opción **Contraseña al abrir** y para abrir el documento no será necesario escribir la contraseña.  Si desea que el documento de su solución requiera una contraseña para poder abrirse, deberá habilitar la opción **Contraseña al abrir** después de realizar la compilación final y antes de implementar la solución.  
  
## Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Información general sobre la administración de permisos sobre la información y las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Cómo: Permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  