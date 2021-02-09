---
title: Enlazar controles de WPF a datos (parte 1)
description: Enlazar controles de WPF a datos. Para crear estos controles enlazados a datos, arrastre los elementos desde la ventana orígenes de datos hasta WPF Designer en Visual Studio.
ms.custom: SEO-VS-2020
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 137d8970ebfc70dcf102fa70d7bcf18d81677535
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859273"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Enlace de controles de WPF a datos en Visual Studio

Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Para crear estos controles enlazados a datos, puede arrastrar elementos desde la ventana **orígenes de datos** hasta el [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] en Visual Studio. En este tema se describen algunas de las tareas, herramientas y clases más comunes que se pueden usar para crear aplicaciones de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] enlazadas a datos.

Para obtener información general sobre cómo crear controles enlazados a datos en Visual Studio, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obtener más información sobre el [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] enlace de datos, vea [información general](/dotnet/desktop-wpf/data/data-binding-overview)sobre el enlace de datos.

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Tareas necesarias para enlazar controles WPF a datos

En la tabla siguiente se enumeran las tareas que se pueden realizar al arrastrar elementos desde la ventana **Orígenes de datos** hasta [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Tarea|Más información|
|----------| - |
|Crear nuevos controles enlazados a datos.<br /><br /> Enlazar controles existentes a datos.|[Enlazar controles de WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Crear controles que muestren los datos relacionados de una relación primaria-secundaria: cuando el usuario selecciona un registro de datos primario en un control, otro control muestra los datos secundarios relacionados correspondientes al registro seleccionado.|[Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Crear una *tabla de búsqueda* que muestre información de una tabla según el valor de un campo de clave externa de otra tabla.|[Creación de tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Enlazar un control a una imagen de una base de datos.|[Enlazar controles a imágenes desde una base de datos](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Destinos de colocación válidos

Los elementos de la ventana **Orígenes de datos** solo se pueden arrastrar hasta destinos de colocación válidos de [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Principalmente, existen dos tipos de destinos para colocar válidos: contenedores y controles. Un contenedor es un elemento de la interfaz de usuario que normalmente contiene controles. Por ejemplo, una cuadrícula es un contenedor, como también lo es una ventana.

## <a name="generated-xaml-and-code"></a>Código y XAML generado

Al arrastrar un elemento desde la ventana **orígenes de datos** hasta el [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] , Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que define un nuevo control enlazado a datos (o enlaza un control existente al origen de datos). En algunos orígenes de datos, Visual Studio también genera código en el archivo de código subyacente que rellena el origen de datos con datos.

En la tabla siguiente se muestra el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] código y que genera Visual Studio para cada tipo de origen de datos en la ventana **orígenes de datos** .

| Origen de datos | Genera XAML que enlaza un control al origen de datos | Genera código que llena de datos el origen de datos |
| - | - | - |
| Dataset | Sí | Sí |
| [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] | Sí | Sí |
| Servicio | Sí | No |
| Object | Sí | No |

### <a name="datasets"></a>Conjuntos de datos

Cuando se arrastra una tabla o columna desde la ventana **orígenes de datos** hasta el diseñador, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lo siguiente:

- Agrega el conjunto de datos y un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos del conjunto de datos.

- Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el XAML enlaza el control al elemento. Si arrastra el elemento hasta un contenedor, el código XAML crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

Visual Studio también realiza los cambios siguientes en el archivo de código subyacente:

- Crea un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded> para el elemento de [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contiene el control. El controlador de eventos llena de datos la tabla, recupera <xref:System.Windows.Data.CollectionViewSource> de los recursos del contenedor y, a continuación, convierte el primer elemento de datos en el elemento actual. Si <xref:System.Windows.FrameworkElement.Loaded> ya existe un controlador de eventos, Visual Studio agrega este código al controlador de eventos existente.

### <a name="entity-data-models"></a>Entity Data Models

Al arrastrar una entidad o una propiedad de entidad desde la ventana **orígenes de datos** hasta el diseñador, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lo siguiente:

- Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos de la entidad.

- Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] enlaza el control al elemento. Si arrastra el elemento hasta un contenedor, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

Visual Studio también realiza los cambios siguientes en el archivo de código subyacente:

- Agrega un nuevo método que devuelve una consulta para la entidad que se arrastró hasta el diseñador (o la entidad que contiene la propiedad que se arrastró hasta el diseñador). El nuevo método tiene el nombre `Get<EntityName>Query` , donde `\<EntityName>` es el nombre de la entidad.

- Crea un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded> para el elemento de [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contiene el control. El controlador de eventos llama al `Get<EntityName>Query` método para rellenar la entidad con datos, recupera <xref:System.Windows.Data.CollectionViewSource> de los recursos del contenedor y, a continuación, convierte el primer elemento de datos en el elemento actual. Si <xref:System.Windows.FrameworkElement.Loaded> ya existe un controlador de eventos, Visual Studio agrega este código al controlador de eventos existente.

### <a name="services"></a>Servicios

Al arrastrar un objeto de servicio o una propiedad desde la ventana **orígenes de datos** hasta el diseñador, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que crea un control enlazado a datos (o enlaza un control existente al objeto o la propiedad). Sin embargo, Visual Studio no genera código que llene el objeto de servicio de proxy con datos. Este código se debe escribir expresamente. Para obtener un ejemplo que muestra cómo hacerlo, vea [enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

Visual Studio genera XAML que realiza lo siguiente:

- Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos en el objeto devuelto por el servicio.

- Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] enlaza el control al elemento. Si arrastra el elemento hasta un contenedor, [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>de la empresa

Cuando se arrastra un objeto o una propiedad desde la ventana **orígenes de datos** hasta el diseñador, Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que crea un control enlazado a datos (o enlaza un control existente al objeto o la propiedad). Sin embargo, Visual Studio no genera código para rellenar el objeto con datos. Este código se debe escribir expresamente.

> [!NOTE]
> Las clases personalizadas deben ser públicas y, de forma predeterminada, tener un constructor sin parámetros. No pueden ser clases anidadas que tengan un "punto" en su sintaxis. Para obtener más información, vea [XAML y clases personalizadas para WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

Visual Studio genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] lo siguiente:

- Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos del objeto.

- Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el XAML enlaza el control al elemento. Si arrastra el elemento hasta un contenedor, el código XAML crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
