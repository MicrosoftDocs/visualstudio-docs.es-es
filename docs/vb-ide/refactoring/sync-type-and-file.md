---
title: "Sincronización de tipo y nombre de archivo - refactorización (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff86d7bd-837b-4664-b0ea-d3ee0c52fe87
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 307e8da9c662c4aeeedb1607e45d32fc79956f5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>Sincronizar un tipo en un nombre de archivo o un nombre de archivo a un tipo en Visual Basic

<!-- VERSIONLESS -->
**Esta característica está disponible en Visual Studio de 2017 y versiones posteriores.  Además, los proyectos de .NET estándar no se admiten todavía para esta refactorización.**

**¿Qué:** permite cambiar el nombre de un tipo para que coincida con el nombre de archivo, o bien cambiar el nombre de un nombre de archivo para que coincida con el texto que contiene.

**Cuándo:** ha cambiado el nombre un archivo o un tipo y aún no ha actualizado el archivo correspondiente o el tipo para que coincida con. 

**Por este motivo:** coloca un tipo en un archivo con un nombre diferente, o viceversa, lo difícil encontrar lo está buscando.  Al cambiar el nombre del tipo o nombre de archivo, código pasa a ser más legible y más fácil navegar.

**Cómo:**

1. Resalte o coloque el cursor de texto en el nombre del tipo para sincronizar:

   ![Código que aparece resaltado](media/synctype_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre archivo para *TypeName*.vb** desde la ventana emergente la ventana de vista previa, donde *TypeName* es el nombre del tipo que ha seleccionado.
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre de tipo para _Filename_**  desde la ventana emergente la ventana de vista previa, donde *Filename* es el nombre del archivo actual.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre archivo para *TypeName*.vb** desde la ventana emergente la ventana de vista previa, donde *TypeName* es el nombre del tipo que ha seleccionado.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre de tipo para _Filename_**  desde la ventana emergente la ventana de vista previa, donde  *Nombre de archivo* es el nombre del archivo actual.

   Al instante se cambiará el tipo o el archivo.  En el ejemplo siguiente, el archivo **Employee.vb** se ha cambiado a **Person.vb** para que coincida con el nombre de tipo.

   ![Resultados inline](media/synctype_result.png)

## <a name="see-also"></a>Vea también  
[Refactorización (Visual Basic)](../refactoring-vb.md)
