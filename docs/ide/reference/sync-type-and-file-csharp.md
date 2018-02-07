---
title: Cambio del nombre de un archivo para que coincida con un tipo de C# en Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ada7044ebb6718dc0380b387a130ea7b2334e443
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Sincronización de un tipo con un nombre de archivo, o de un nombre de archivo con un tipo en C# #

<!-- VERSIONLESS -->
**Esta característica está disponible en Visual Studio 2017 y versiones posteriores.  Además, los proyectos de .NET Standard no se admiten todavía para esta refactorización.**

**Qué:** Le permite cambiar el nombre de un tipo para que coincida con el nombre de archivo, o bien cambiar el nombre de un archivo para que coincida con el tipo que contiene.

**Cuándo:** Ha cambiado el nombre un archivo o un tipo y aún no ha actualizado aún el archivo o el tipo correspondiente para que coincidan. 

**Por qué:** El hecho de colocar un tipo en un archivo con un nombre diferente, o viceversa, dificulta encontrar lo que está buscando.  Al cambiar el nombre del tipo o del archivo, es más fácil leer el código y navegar hasta él.

**Cómo**:

1. Resalte o coloque el cursor de texto en el nombre del tipo que se va a sincronizar:

   ![Código resaltado](media/synctype-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar nombre de archivo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar nombre de tipo a _NombreArchivo_.cs** en el menú emergente de la ventana Vista previa, donde *NombreArchivo* es el nombre del archivo actual.
   * **Mouse**
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar nombre de archivo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
     * Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar nombre de tipo a _NombreArchivo_.cs** en el menú emergente de la ventana Vista previa, donde *NombreArchivo* es el nombre del archivo actual.

   Al instante se cambiará el nombre del tipo o el archivo.  En el ejemplo siguiente, el nombre de archivo **MyClass.cs** se ha cambiado a **MyNewClass.cs** para que coincida con el nombre de tipo.

   ![Resultado en línea](media/synctype-result-cs.png)

## <a name="see-also"></a>Vea también

[Refactorización](../refactoring-in-visual-studio.md)
