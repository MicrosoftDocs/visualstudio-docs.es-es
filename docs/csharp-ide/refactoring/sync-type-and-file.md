---
title: "Sincronización de tipo y nombre de archivo - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48172dd7-24a5-4884-8a73-f92497ad6a0d
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: ee37983575aa82abb764d57006cdabd094ea6497
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Sincronizar un tipo en un nombre de archivo o un nombre de archivo a un tipo de C# #

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
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre archivo para *TypeName*.cs** desde la ventana emergente la ventana de vista previa, donde *TypeName* es el nombre del tipo que ha seleccionado.
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre de tipo para _Filename_**  desde la ventana emergente la ventana de vista previa, donde *Filename* es el nombre del archivo actual.
   * **Mouse**
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre archivo para *TypeName*.cs** desde la ventana emergente la ventana de vista previa, donde *TypeName* es el nombre del tipo que ha seleccionado.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **cambiar el nombre de tipo para _Filename_**  desde la ventana emergente la ventana de vista previa, donde  *Nombre de archivo* es el nombre del archivo actual.

   Al instante se cambiará el tipo o el archivo.  En el ejemplo siguiente, el archivo **MyClass.cs** se ha cambiado a **MyNewClass.cs** para que coincida con el nombre de tipo.

   ![Resultados inline](media/synctype_result.png)

## <a name="see-also"></a>Vea también  
[Refactorización (C#)](../refactoring-csharp.md)
