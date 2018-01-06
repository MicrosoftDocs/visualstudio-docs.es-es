---
title: "Visualización de archivos mediante el abierto con el comando | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a1631632a2ceb66380d1d0c41e54b5a4244a31a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Visualización de archivos mediante el abierto con el comando
Un proyecto puede pedir el IDE para mostrar el **abrir con** cuadro de diálogo. Esta solicitud pide al usuario que abra un archivo que tenga una selección de editores estándares. Los pasos siguientes describen este proceso.  
  
1.  Las llamadas de proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, especificando un valor de OSE_UseOpenWithDialog para el `OSEOpenDocEditor` parámetro.  
  
2.  En función de la extensión de nombre de archivo del documento, el IDE determina qué editores aparecen en el puede registro abran el documento especificado y muestra esta información en el **abrir con** cuadro de diálogo.  
  
    > [!NOTE]
    >  Los proyectos que tienen un editor intrínseco que debe incluirse en la **abrir con** cuadro de diálogo debe registrar un generador de editores de cada editor de este tipo. Intrínsecos editores solo funcionan junto con un determinado tipo de proyecto, que se aplica en la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. El IDE incluye una fábrica de editor integrada para el editor de texto básico y el editor binario. El IDE también crea una instancia de un generador de editores en nombre de cada asociación de archivo registrado de Windows. Un ejemplo de este archivo es Microsoft Word.  
  
3.  Tan pronto como el usuario selecciona un elemento de la **abrir con** cuadro de diálogo, el IDE, a continuación, abre el documento mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método. Para obtener más información, consulte [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vea también  
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)