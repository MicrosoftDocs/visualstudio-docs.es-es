---
title: "Visualizaci&#243;n de archivos mediante el abrir con el comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto, compatibilidad con el comando Abrir con"
  - "Comando Abrir con"
  - "persistencia, compatibilidad con el comando Abrir con"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Visualizaci&#243;n de archivos mediante el abrir con el comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un proyecto puede formular el IDE para mostrar el cuadro de diálogo de **Abrir con** .  Esta solicitud pide al usuario abrir un archivo con una selección de editores estándar.  los pasos siguientes describen este proceso.  
  
1.  El proyecto llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, especificando un valor de OSE\_UseOpenWithDialog para el parámetro de `OSEOpenDocEditor` .  
  
2.  Basándose en la extensión de nombre de archivo del documento, el IDE determina que los editores enumerados en el registro pueden abrir el documento especificado y muestra esta información en el cuadro de diálogo de **Abrir con** .  
  
    > [!NOTE]
    >  Los proyectos que tienen un editor intrínseco que se debe incluir en el cuadro de diálogo de **Abrir con** deben registrar un generador del editor para cada uno editor.  Los editores intrínsecos solo funcionan junto con un tipo determinado de proyecto, que se aplica en la implementación del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  El IDE incluye un generador integrada del editor para el editor de texto básico y el editor binario.  El IDE también crea una instancia de un generador del editor en nombre de cada asociación de archivo registrada de Windows.  Un ejemplo de este tipo de archivo es Microsoft Word.  
  
3.  En cuanto el usuario selecciona un elemento del cuadro de diálogo de **Abrir con** , el IDE abra el documento llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  Para obtener más información, vea [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md).  
  
## Vea también  
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md)