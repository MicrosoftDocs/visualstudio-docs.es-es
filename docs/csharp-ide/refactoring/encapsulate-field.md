---
title: "Encapsular campo - refactorización (C#) | Documentos de Microsoft"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 59b71a0716415dcedeab9954486ef27e0fc438d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="encapsulate-a-field-in-c"></a>Encapsular un campo en C# #
**¿Qué:** le permite convertir un campo en una propiedad y actualizar todos los usos de ese campo se utiliza la propiedad recién creada.

**Cuándo:** que desea mover un campo en una propiedad y actualizar todas las referencias a ese campo.  

**Por este motivo:** desee proporcionar acceso de otras clases a un campo, pero no desea que esas clases para tener acceso directo.  Al ajustar el campo en una propiedad, puede escribir código para comprobar el valor asignado, por ejemplo.

**Cómo:**

1. Resalte o coloque el cursor de texto en el nombre del campo para encapsular:

   ![Código que aparece resaltado](media/encapsulate_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **CTRL+e**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **encapsular campo** entrada desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Seleccione **Editar > refactorizar > encapsular campo**.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **encapsular campo** entrada desde la ventana emergente de ventana de vista previa.

   Selección | Descripción
   --------- | -----------
   **Encapsular campo (y utiliza la propiedad)** | Encapsula el campo con una propiedad y actualiza todos los usos del campo que desee utilizar la propiedad generada
   **Encapsular campo (pero sin utilizar campo)** | Encapsula el campo con una propiedad, pero deja intactos todos los usos del campo

   La propiedad se creará inmediatamente y se actualizarán las referencias al campo, si ha seleccionado.

   > [!TIP]
   > Use la [ **obtener una vista previa de cambios** ](../../ide/preview-changes.md) vínculo en la ventana emergente para ver cuál será el resultado antes de confirmar a él.

   ![Encapsular el resultado de la propiedad](media/encapsulate_result.png)

## <a name="see-also"></a>Vea también  
[Refactorización (C#)](../refactoring-csharp.md)  
[Vista previa de cambios](../../ide/preview-changes.md)