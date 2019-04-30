---
title: Mostrar datos relacionados en aplicaciones WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da6f276e714c816ea9b3c1b735ad50f31ffdc3c0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567070"
---
# <a name="display-related-data-in-wpf-applications"></a>Mostrar datos relacionados en aplicaciones WPF

En algunas aplicaciones, es posible que desea trabajar con datos procedentes de varias tablas o entidades que se relacionan entre sí en una relación de elementos primarios y secundarios. Por ejemplo, desea mostrar una cuadrícula que muestra los clientes de un `Customers` tabla. Cuando el usuario selecciona un cliente específico, otra cuadrícula muestra los pedidos para ese cliente desde un relacionados `Orders` tabla.

Puede crear controles enlazados a datos que muestran datos relacionados arrastrando elementos desde la **orígenes de datos** ventana hasta WPF Designer.

## <a name="to-create-controls-that-display-related-records"></a>Para crear controles que muestren los registros relacionados

1. En el menú **Datos**, haga clic en **Mostrar orígenes de datos** para abrir la ventana **Orígenes de datos**.

2. Haga clic en **Agregar nuevo origen de datos** y complete el **Asistente para configuración de orígenes de datos**.

3. Abra el diseñador WPF y asegúrese de que el diseñador contiene un contenedor que sea un destino válido para los elementos de la **orígenes de datos** ventana.

     Para obtener más información acerca de los destinos de colocación válidos, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. En el **orígenes de datos** ventana, expanda el nodo que representa la tabla primaria o de objeto en la relación. La tabla primaria o el objeto se encuentra en el lado "uno" de una relación uno a varios.

5. Arrastre el nodo primario (o cualquier elemento individual en el nodo primario) desde el **orígenes de datos** ventana a un destino válido en el diseñador.

     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada elemento que se arrastra. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla primaria o el objeto a los recursos de destino. Para algunos orígenes de datos, Visual Studio también genera código para cargar los datos en la tabla u objeto primario. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. En el **orígenes de datos** ventana, busque la tabla secundaria relacionada o el objeto. Objetos y las tablas secundarias relacionadas aparecen como nodos expansibles en la parte inferior de la lista del nodo primario de los datos.

7. Arrastre el nodo secundario (o cualquier elemento individual en el nodo secundario) desde el **orígenes de datos** ventana a un destino válido en el diseñador.

     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos arrastrados. El XAML también agrega un nuevo <xref:System.Windows.Data.CollectionViewSource> para la tabla u objeto secundario a los recursos de destino. Esta nueva <xref:System.Windows.Data.CollectionViewSource> está enlazado a la propiedad de la tabla primaria o el objeto que acaba de arrastrar al diseñador. Para algunos orígenes de datos, Visual Studio también genera código para cargar los datos en la tabla u objeto secundario.

     En la siguiente ilustración se muestra que se relaciona **pedidos** tabla de la **clientes** tabla en un conjunto de datos en el **orígenes de datos** ventana.

     ![Ventana Orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)