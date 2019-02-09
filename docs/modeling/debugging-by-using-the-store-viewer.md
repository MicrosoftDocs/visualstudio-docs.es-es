---
title: Depurar con el visor de almacén
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fb03dd67168867026c77a30bba412076c0b8408
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945322"
---
# <a name="debugging-by-using-the-store-viewer"></a>Depurar con el visor de almacén
Con el Visor de Store, puede examinar el estado de un *almacenar* usando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. El Visor Store muestra todos los elementos de modelo de dominio que se encuentran en un almacén específico, junto con vínculos entre los elementos y propiedades del elemento.

## <a name="opening-store-viewer"></a>Visor de apertura Store
 Cuando esté en la compilación experimental de Visual Studio, detenga el código en un punto de interrupción donde una instancia del almacén contiene información sobre el modelo. A continuación, abra el Visor de Store escribiendo el siguiente comando en el **inmediato** ventana:

```csharp
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
>  Debe reemplazar `mystore` con el nombre de la instancia de almacén. Además, si agrega el espacio de nombres en el código, puede escribir el comando para mostrar el Visor de Store sin el espacio de nombres completo:
>
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
>  `...`
>
>  `StoreViewer.Show(mystore);`

 El `Show` método tiene varias sobrecargas. Puede especificar una instancia de un almacén o una partición como parámetro.

 Como alternativa, puede colocar la línea de código que muestra el Visor de Store en cualquier lugar del código donde el parámetro que se pasa a la `Show` método está en el ámbito. Esta acción muestra el Visor Store cuando se ejecuta la línea de código como una instantánea del contenido de la tienda.

### <a name="using-store-viewer"></a>Mediante el Visor de Store
 Cuando se abre el Visor de Store, aparecerá una ventana de Windows Forms no modal, como se muestra en la ilustración siguiente.

 ![](../modeling/media/storeviewer2.png) Visor de Store

 El Visor de Store tiene tres paneles: el panel izquierdo, el panel de la parte superior derecha y el panel inferior derecho. El panel izquierdo es una vista de árbol de los tipos en el `DomainDataDirectory` miembro de un almacén. Si expande el nodo de partición y haga clic en un elemento, las propiedades del elemento aparecen en el panel de la parte superior derecha. Si el elemento está vinculado a otros elementos, aparecen los elementos adicionales en el panel de la esquina inferior derecha. Si hace doble clic en un elemento en el panel de la esquina inferior derecha, el elemento está resaltado en el panel izquierdo.

## <a name="see-also"></a>Vea también

- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)