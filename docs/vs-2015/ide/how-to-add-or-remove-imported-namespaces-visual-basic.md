---
title: 'Cómo: Agregar o quitar espacios de nombres importados (Visual Basic) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75299dae66a07b2bc1671dbfcda935fc4af2b284
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645495"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Cómo: Agregar o quitar espacios de nombres importados (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Importar un espacio de nombres le permite usar elementos de ese espacio de nombres en su código sin calificar completamente el elemento. Por ejemplo, si quiere tener acceso al método `Create` en la clase `System.Messaging.MessageQueue`, puede importar el espacio de nombres `System.Messaging` y simplemente hacer referencia al elemento que necesita en el código como `MessageQueue.Create`.

 Los espacios de nombres importados se administran en la página **Referencias** del **Diseñador de proyectos**. Las importaciones que especifique en este cuadro de diálogo se pasan directamente al compilador (`/imports`) y se aplican a todos los archivos de su proyecto. Use la instrucción `Imports` para usar un espacio de nombres en un archivo de código fuente único.

### <a name="to-add-an-imported-namespace"></a>Para agregar un espacio de nombres importado

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En la lista **Espacios de nombres importados**, seleccione la casilla del espacio de nombres que quiere agregar.

    > [!NOTE]
    > Para importarse, el espacio de nombres debe estar en un componente al que se hace referencia. Si el espacio de nombres no aparece en la lista, necesitará agregar una referencia al componente que lo contiene. Para obtener más información, consulte [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

### <a name="to-remove-an-imported-namespace"></a>Para quitar un espacio de nombres importado

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En la lista **Espacios de nombres importados**, desactive la casilla del espacio de nombres que quiere quitar.

## <a name="user-imports"></a>Importaciones de usuarios
 Las importaciones de usuarios le permiten importar una clase específica dentro de un espacio de nombres en lugar del espacio de nombres completo. Por ejemplo, su aplicación puede tener una importación para el espacio de nombres `Systems.Diagnostics`, pero la única clase dentro de ese espacio de nombres en la que está interesado es la clase `Debug`. Puede definir `System.Diagnostics.Debug` como una importación de usuarios y, después, quitar la importación para `System.Diagnostics`.

 Si posteriormente cambia de idea y decide que realmente necesitaba la clase `EventLog`, puede especificar `System.Diagnostics.EventLog` como una importación de usuarios y sobrescribir `System.Diagnostics.Debug` con la función de actualización.

#### <a name="to-add-a-user-import"></a>Para agregar una importación de usuarios

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En el cuadro de texto debajo de la lista **Espacios de nombres importados**, escriba el nombre completo del espacio de nombres que quiere importar, incluido el espacio de nombres raíz.

4. Haga clic en el botón **Agregar importación del usuario** para agregar el espacio de nombres a la lista **Espacios de nombres importados**.

    > [!NOTE]
    > El botón **Agregar importación del usuario** se deshabilitará si el espacio de nombres coincide con uno que ya está en la lista; no puede agregar una importación dos veces.

#### <a name="to-update-a-user-import"></a>Para actualizar una importación de usuarios

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En la lista **Espacios de nombres importados**, seleccione el espacio de nombres que quiere cambiar.

4. En el cuadro de texto debajo de la lista **Espacios de nombres importados**, escriba el nombre del nuevo espacio de nombres.

5. Haga clic en el botón **Actualizar importación del usuario** para actualizar el espacio de nombres en la lista **Espacios de nombres importados**.

## <a name="see-also"></a>Vea también
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)
