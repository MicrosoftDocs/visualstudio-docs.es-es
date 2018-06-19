---
title: Enlazar controles WPF a datos en Visual Studio - parte 1 | Documentos de Microsoft
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7674656c9a4995b853753e12b19fd71bf77a3c9f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926750"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Enlazar controles WPF a datos en Visual Studio
Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Para crear estos controles enlazados a datos, puede arrastrar elementos desde la **orígenes de datos** ventana hasta el [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En este tema se describen algunas de las tareas, herramientas y clases más comunes que se pueden usar para crear aplicaciones de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] enlazadas a datos.

 Para obtener información general sobre cómo crear controles enlazados a datos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obtener más información acerca de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] enlace de datos, vea [información general sobre el enlace de datos](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Tareas necesarias para enlazar controles WPF a datos
 En la tabla siguiente se enumera las tareas que se pueden realizar al arrastrar elementos desde la **orígenes de datos** ventana para el [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].

|Tarea|Más información|
|----------|----------------------|
|Crear nuevos controles enlazados a datos.<br /><br /> Enlazar controles existentes a datos.|[Enlazar controles de WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Crear controles que muestren los datos relacionados de una relación primaria-secundaria: cuando el usuario selecciona un registro de datos primario en un control, otro control muestra los datos secundarios relacionados correspondientes al registro seleccionado.|[Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Crear un *tabla de búsqueda* que muestra información de una tabla basada en el valor de un campo de clave externa de otra tabla.|[Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Enlazar un control a una imagen de una base de datos.|[Enlazar controles a imágenes desde una base de datos](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Destinos de colocación válidos
 Puede arrastrar elementos en la **orígenes de datos** ventana sólo a destinos de colocación válidos en el [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Principalmente, existen dos tipos de destinos para colocar válidos: contenedores y controles. Un contenedor es un elemento de la interfaz de usuario que normalmente contiene controles. Por ejemplo, una cuadrícula es un contenedor, como también lo es una ventana.

## <a name="generated-xaml-and-code"></a>XAML y el código generado
 Cuando se arrastra un elemento de la **orígenes de datos** ventana para el [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que define un nuevo control enlazado a datos (o enlaza un control existente al origen de datos). En el caso de algunos orígenes de datos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] también genera código en el archivo de código subyacente que llena de datos el origen de datos.

 La siguiente tabla se recogen los [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] y el código que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera para cada tipo de origen de datos en el **orígenes de datos** ventana.

|Origen de datos|Genera XAML que enlaza un control al origen de datos|Genera código que llena de datos el origen de datos|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Conjunto de datos|Sí|Sí|
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Sí|Sí|
|web de Office|Sí|No|
|Object|Sí|No|

### <a name="datasets"></a>Conjuntos de datos
 Cuando se arrastra una tabla o columna de la **orígenes de datos** ventana hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que realiza lo siguiente:

-   Agrega el conjunto de datos y un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos del conjunto de datos.

-   Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el XAML enlaza el control al elemento. Si arrastra el elemento a un contenedor, el XAML crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] también realiza los cambios siguientes en el archivo de código subyacente:

-   Crea un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded> para el elemento de [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contiene el control. El controlador de eventos llena de datos la tabla, recupera <xref:System.Windows.Data.CollectionViewSource> de los recursos del contenedor y, a continuación, convierte el primer elemento de datos en el elemento actual. Si un <xref:System.Windows.FrameworkElement.Loaded> ya existe un controlador de eventos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agrega este código al controlador de eventos existente.

### <a name="entity-data-models"></a>Entity data Model
 Cuando se arrastra una entidad o una propiedad de entidad desde la **orígenes de datos** ventana hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que realiza lo siguiente:

-   Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos de la entidad.

-   Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] enlaza el control al elemento. Si arrastra el elemento a un contenedor, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

Visual Studio también realiza los cambios siguientes en el archivo de código subyacente:

-   Agrega un nuevo método que devuelve una consulta para la entidad que se arrastró hasta el diseñador (o la entidad que contiene la propiedad que se arrastró hasta el diseñador). El nuevo método tiene el nombre Get*EntityName*consulta, donde *EntityName* es el nombre de la entidad.

-   Crea un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded> para el elemento de [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contiene el control. El controlador de eventos llama a Get*EntityName*consultar método para llenar la entidad con datos, recupera el <xref:System.Windows.Data.CollectionViewSource> desde el contenedor recursos y, a continuación, convierte el primer elemento de datos del elemento actual. Si un <xref:System.Windows.FrameworkElement.Loaded> ya existe un controlador de eventos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agrega este código al controlador de eventos existente.

### <a name="services"></a>Servicios
 Cuando se arrastra un objeto de servicio o una propiedad de la **orígenes de datos** ventana hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que crea un control enlazado a datos (o enlaza un control existente al objeto o la propiedad). Sin embargo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no genera código que llene de datos el objeto de servicio del proxy. Este código se debe escribir expresamente. Para obtener un ejemplo que muestra cómo hacerlo, consulte [WPF enlazar controles a un servicio de datos WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio genera XAML que realiza lo siguiente:

-   Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos en el objeto devuelto por el servicio.

-   Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] enlaza el control al elemento. Si arrastra el elemento a un contenedor, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>de la empresa
 Cuando se arrastra un objeto o una propiedad de la **orígenes de datos** ventana hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que crea un control enlazado a datos (o enlaza un control existente al objeto o la propiedad). Sin embargo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no genera el código que llena de datos el objeto. Este código se debe escribir expresamente.

> [!NOTE]
>  Las clases personalizadas deben ser públicos y, de forma predeterminada, tienen un constructor sin parámetros. Además, las clases de can'tbe anidados que tienen un "punto" en su sintaxis. Para obtener más información, consulte [clases XAML y personalizadas para WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que realiza lo siguiente:

-   Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento. <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos del objeto.

-   Crea un enlace de datos para un control. Si se arrastra el elemento hasta un control existente en el diseñador, el XAML enlaza el control al elemento. Si arrastra el elemento a un contenedor, el XAML crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento. El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)