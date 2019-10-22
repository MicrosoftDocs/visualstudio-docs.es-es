---
title: Depuración mediante el visor de la tienda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654890"
---
# <a name="debugging-by-using-the-store-viewer"></a>Depurar con el visor de almacén
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con el visor de la tienda, puede examinar el estado de un *almacén* usado por [!INCLUDE[dsl](../includes/dsl-md.md)]. El visor de la tienda muestra todos los elementos del modelo de dominio que se encuentran en un almacén específico, junto con las propiedades del elemento y los vínculos entre los elementos.

## <a name="opening-store-viewer"></a>Abrir el visor de almacén
 Cuando esté en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] compilación experimental, detenga el código en un punto de interrupción en el que una instancia del almacén contenga información del modelo. A continuación, abra el visor de la tienda escribiendo el siguiente comando en la ventana **inmediato** :

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> Debe reemplazar `mystore` por el nombre de la instancia de Store. Además, si agrega el espacio de nombres al código, puede escribir el comando para mostrar el visor del almacén sin el espacio de nombres completo:
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 El método `Show` tiene varias sobrecargas. Puede especificar una instancia de un almacén o una partición como parámetro.

 Como alternativa, puede colocar la línea de código que muestra el visor del almacén en cualquier lugar del código donde el parámetro que se pasa al método `Show` está en el ámbito. Esta acción muestra el visor de almacén cuando la línea de código se ejecuta como una instantánea del contenido del almacén.

### <a name="using-store-viewer"></a>Uso del visor de almacén
 Cuando se abre el visor de almacén, aparece una ventana de Windows Forms no modal, tal como se muestra en la siguiente ilustración.

 ![](../modeling/media/storeviewer2.png "storeviewer2")Visor de tienda

 El visor de la tienda tiene tres paneles: el panel izquierdo, el panel superior derecho y el panel inferior derecho. El panel izquierdo es una vista de árbol de los tipos del `DomainDataDirectory` miembro de un almacén. Si expande el nodo de partición y hace clic en un elemento, las propiedades del elemento aparecen en el panel superior derecho. Si el elemento está vinculado a otros elementos, los elementos adicionales aparecen en el panel inferior derecho. Si hace doble clic en un elemento del panel de la parte inferior derecha, el elemento se resalta en el panel izquierdo.

## <a name="see-also"></a>Vea también
 [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
