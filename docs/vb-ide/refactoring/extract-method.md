---
title: "Extraer método - refactorización (Visual Basic) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 6ec25b8c0e2a583364ff3c6418515507cdc04d40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-visual-basic"></a>Extraer un método en Visual Basic
**¿Qué:** le permite convertir un fragmento de código en su propio método.

**Cuándo:** tiene un fragmento de código existente en algún método que debe llamarse desde otro método.  

**Por este motivo:** se puede copiar y pegar ese código, pero esto conduciría a la duplicación.  Una mejor solución consiste en refactorizar ese fragmento en su propio método que se puede llamar libremente con cualquier otro método.

**Cómo:**

1. Resalte el código que se va a extraer:

   ![Código que aparece resaltado](media/extractmethod_highlight.png)

1. A continuación, realice una de las siguientes acciones:
   * **Teclado**
     * Presione **Ctrl + R**, a continuación, **Ctrl + M**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
     * Presione **Ctrl +.** Para activar el **acciones rápidas y refactorizaciones** menú y seleccione **Extraer método** desde la ventana emergente de ventana de vista previa.
   * **Mouse**
     * Seleccione **Editar > refactorizar > Extraer método**.
     * Haga clic en el código y seleccione **refactorizar > Extraer > Extraer método**.
     * Haga clic en el código, seleccione la **acciones rápidas y refactorizaciones** menú y seleccione **Extraer método** desde la ventana emergente de ventana de vista previa.

   Se creará inmediatamente el método.  Desde aquí, ahora puede cambiar el nombre del método, simplemente escribiendo el nuevo nombre.

   > [!TIP]
   > También puede actualizar los comentarios y otras cadenas para usar este nuevo nombre, así como [obtener una vista previa de cambios](../../ide/preview-changes.md) antes de guardar, mediante las casillas de verificación en la **cambiar el nombre de** cuadro que aparece en la parte superior derecha de su IDE.

   ![Cambiar el nombre de método](media/extractmethod_rename.png)

1. Cuando esté satisfecho con el cambio, haga clic en el **aplicar** o presionen **ENTRAR** y los cambios se confirmarán.

## <a name="see-also"></a>Vea también  
[Refactorización (Visual Basic)](../refactoring-vb.md)  
[Vista previa de cambios](../../ide/preview-changes.md)