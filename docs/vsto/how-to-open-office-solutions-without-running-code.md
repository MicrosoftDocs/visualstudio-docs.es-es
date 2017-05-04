---
title: "C&#243;mo: Abrir soluciones de Office sin ejecutar c&#243;digo | Microsoft Docs"
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
  - "ensamblados [desarrollo de Office en Visual Studio], omitir"
  - "excluir ensamblados"
  - "documentos [desarrollo de Office en Visual Studio], abrir sin ejecutar código"
  - "documentos de Office [desarrollo de Office en Visual Studio], abrir sin ejecutar código"
  - "soluciones de Office [desarrollo de Office en Visual Studio], abrir"
  - "abrir soluciones de Office"
  - "soluciones [desarrollo de Office en Visual Studio], abrir"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Abrir soluciones de Office sin ejecutar c&#243;digo
  Una solución de Microsoft Office creada con extensiones de código administrado se ejecutará aunque la configuración de seguridad de la aplicación de Office del usuario final esté establecida en Alta.  Esto obedece a que la seguridad del código de ensamblado de .NET es administrada por Microsoft .NET Framework y no por Microsoft Office.  
  
 No obstante, pueden existir varios motivos que aconsejen abrir un documento sin ejecutar el código.  Por ejemplo, el código que se ejecuta cuando se abre el documento podría alterar el contenido, pero el usuario desea actualizar el aspecto del documento antes de que el código lo cambie.  O bien, quizás desee enviar a alguien el documento con determinada información y no desee ejecutar el código y, posiblemente, alterar el contenido.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Existen varias formas de abrir un documento o un libro que contenga extensiones de código administrado sin ejecutar el código de ensamblado.  
  
### Para omitir el ensamblado usando la tecla MAYÚS  
  
-   Abra los documentos y libros desde el menú **Archivo** manteniendo presionada la tecla MAYÚS para evitar que Word y Excel provoquen eventos de inicialización mientras el documento está abriéndose.  
  
    > [!NOTE]  
    >  Si abre un documento o libro desde el panel de tareas **Introducción**, al mantener presionada la tecla MAYÚS no se omite el código.  Asimismo, manteniendo presionada la tecla MAYÚS no se impide que se produzcan eventos después de abrir el documento.  
  
     Este método es útil si desea abrir un documento para realizar cambios sin ejecutar el código y modificar primero el documento.  
  
### Para omitir un ensamblado cambiándole el nombre o quitándolo  
  
-   Si tiene los permisos necesarios en el equipo donde está ubicado el ensamblado, puede quitarlo o cambiar su nombre para que tanto el documento como el libro no puedan encontrarlo.  Esto hace que se produzca un error cada vez que se abre el documento de Office.  
  
     Si la solución es utilizada por varias personas, con este método se impide que la solución se ejecute para todas ellas.  Esto puede resultar útil si se encuentra un problema en el código o en un servidor al que se hace referencia y desea impedir que lo ejecuten todos los usuarios.  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  