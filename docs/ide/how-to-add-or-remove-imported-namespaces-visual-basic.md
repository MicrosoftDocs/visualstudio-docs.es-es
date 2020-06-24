---
title: 'Cómo: Agregar o quitar espacios de nombres importados (Visual Basic)'
ms.date: 06/21/2017
ms.topic: how-to
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a50fdb643029bed8a44ce6999d4a8ce062ba3dcf
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284744"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Cómo: Agregar o quitar espacios de nombres importados (Visual Basic)

Importar un espacio de nombres le permite usar elementos de ese espacio de nombres en su código sin calificar completamente el elemento. Por ejemplo, si quiere tener acceso al método `Create` en la clase `System.Messaging.MessageQueue`, puede importar el espacio de nombres `System.Messaging` y simplemente hacer referencia al elemento que necesita en el código como `MessageQueue.Create`.

Los espacios de nombres importados se administran en la página **Referencias** del **Diseñador de proyectos**. Las importaciones que especifique en este cuadro de diálogo se pasan directamente al compilador ( */imports*) y se aplican a todos los archivos de su proyecto. Use la instrucción `Imports` para usar un espacio de nombres en un archivo de código fuente único.

### <a name="to-add-an-imported-namespace"></a>Para agregar un espacio de nombres importado

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En la lista **Espacios de nombres importados**, seleccione la casilla del espacio de nombres que quiere agregar.

    > [!NOTE]
    > Para importarse, el espacio de nombres debe estar en un componente al que se hace referencia. Si el espacio de nombres no aparece en la lista, necesitará agregar una referencia al componente que lo contiene. Para más información, vea [Administrar referencias en un proyecto](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Para quitar un espacio de nombres importado

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En la lista **Espacios de nombres importados**, desactive la casilla del espacio de nombres que quiere quitar.

## <a name="user-imports"></a>Importaciones de usuarios
Las importaciones de usuarios le permiten importar una clase específica dentro de un espacio de nombres en lugar del espacio de nombres completo. Por ejemplo, su aplicación puede tener una importación para el espacio de nombres <xref:System.Diagnostics>, pero la única clase dentro de ese espacio de nombres en la que está interesado es la clase `Debug`. Puede definir <xref:System.Diagnostics.Debug> como una importación de usuarios y, después, quitar la importación para <xref:System.Diagnostics>.

Si posteriormente cambia de idea y decide que realmente necesitaba la clase `EventLog`, puede especificar <xref:System.Diagnostics.EventLog> como una importación de usuarios y sobrescribir <xref:System.Diagnostics.Debug> con la función de actualización.

### <a name="to-add-a-user-import"></a>Para agregar una importación de usuarios

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En el cuadro de texto debajo de la lista **Espacios de nombres importados**, escriba el nombre completo del espacio de nombres que quiere importar, incluido el espacio de nombres raíz.

4. Haga clic en el botón **Agregar importación del usuario** para agregar el espacio de nombres a la lista **Espacios de nombres importados**.

    > [!NOTE]
    > El botón **Agregar importación del usuario** se deshabilitará si el espacio de nombres coincide con uno que ya está en la lista; no puede agregar una importación dos veces.

### <a name="to-update-a-user-import"></a>Para actualizar una importación de usuarios

1. En el **Explorador de soluciones**, haga doble clic en el nodo **Mi proyecto** del proyecto.

2. En el **Diseñador de proyectos**, haga clic en la pestaña **Referencias**.

3. En la lista **Espacios de nombres importados**, seleccione el espacio de nombres que quiere cambiar.

4. En el cuadro de texto debajo de la lista **Espacios de nombres importados**, escriba el nombre del nuevo espacio de nombres.

5. Haga clic en el botón **Actualizar importación del usuario** para actualizar el espacio de nombres en la lista **Espacios de nombres importados**.

## <a name="see-also"></a>Vea también

- [Administración de referencias en un proyecto](../ide/managing-references-in-a-project.md)
