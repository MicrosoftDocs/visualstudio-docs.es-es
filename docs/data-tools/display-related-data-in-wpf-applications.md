---
title: Mostrar datos relacionados en aplicaciones WPF
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6694d3c1521a6a405323edc33adc44dac0e66829
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282558"
---
# <a name="display-related-data-in-wpf-applications"></a>Mostrar datos relacionados en aplicaciones WPF

En algunas aplicaciones, puede que desee trabajar con datos que proceden de varias tablas o entidades que están relacionadas entre sí en una relación de elementos primarios y secundarios. Por ejemplo, puede que desee mostrar una cuadrícula que muestre los clientes de una `Customers` tabla. Cuando el usuario selecciona un cliente específico, otra cuadrícula muestra los pedidos de ese cliente de una tabla relacionada `Orders` .

Puede crear controles enlazados a datos que muestren los datos relacionados arrastrando elementos desde la ventana **orígenes de datos** hasta WPF Designer.

## <a name="to-create-controls-that-display-related-records"></a>Para crear controles que muestren los registros relacionados

1. En el menú **Datos**, haga clic en **Mostrar orígenes de datos** para abrir la ventana **Orígenes de datos**.

2. Haga clic en **Agregar nuevo origen de datos** y complete el **Asistente para configuración de orígenes de datos**.

3. Abra WPF Designer y asegúrese de que el diseñador contiene un contenedor que es un destino de colocación válido para los elementos de la ventana **orígenes de datos** .

     Para obtener más información sobre los destinos de colocación válidos, vea [enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. En la ventana **orígenes de datos** , expanda el nodo que representa la tabla o el objeto primario de la relación. La tabla o el objeto primario se encuentran en el lado "uno" de una relación de uno a varios.

5. Arrastre el nodo primario (o cualquier elemento individual del nodo primario) desde la ventana **orígenes de datos** hasta un destino de colocación válido en el diseñador.

     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada elemento que se arrastra. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla o el objeto primario a los recursos del destino de colocación. En el caso de algunos orígenes de datos, Visual Studio también genera código para cargar los datos en la tabla o el objeto primario. Para obtener más información, vea [enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. En la ventana **orígenes de datos** , busque la tabla o el objeto secundario relacionado. Las tablas y los objetos secundarios relacionados aparecen como nodos expansibles en la parte inferior de la lista de datos del nodo primario.

7. Arrastre el nodo secundario (o cualquier elemento individual del nodo secundario) desde la ventana **orígenes de datos** hasta un destino de colocación válido en el diseñador.

     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos que se arrastran. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla o el objeto secundario a los recursos del destino de colocación. Este nuevo <xref:System.Windows.Data.CollectionViewSource> se enlaza a la propiedad de la tabla o el objeto primario que acaba de arrastrar al diseñador. En el caso de algunos orígenes de datos, Visual Studio también genera código para cargar los datos en la tabla o el objeto secundario.

     En la siguiente ilustración se muestra la tabla **Orders** relacionada de la tabla **Customers** en un conjunto de datos de la ventana **orígenes de datos** .

     ![Ventana Orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)
