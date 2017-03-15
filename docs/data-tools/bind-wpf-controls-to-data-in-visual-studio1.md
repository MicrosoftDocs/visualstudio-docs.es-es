---
title: "Enlazar controles WPF a datos en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [WPF], mostrar"
  - "enlace de datos, WPF"
  - "mostrar datos, WPF"
  - "WPF [WPF], datos"
  - "enlace de datos de WPF [Visual Studio]"
  - "WPF Designer, enlace de datos"
  - "WPF, enlace de datos en Visual Studio"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Enlazar controles WPF a datos en Visual Studio
Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)].  Para crear estos controles enlazados a datos, puede arrastrar elementos desde la ventana **Orígenes de datos** hasta [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  En este tema se describen algunas de las tareas, herramientas y clases más comunes que se pueden usar para crear aplicaciones de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] enlazadas a datos.  
  
 Para obtener información general sobre el modo de crear controles enlazados a datos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obtener más información sobre el enlace de datos [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)], vea [Información general sobre el enlace de datos](../Topic/Data%20Binding%20Overview.md).  
  
## Tareas necesarias para enlazar controles WPF a datos  
 En la tabla siguiente se enumeran las tareas que se pueden realizar al arrastrar elementos desde la ventana **Orígenes de datos** hasta [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Tarea|Más información|  
|-----------|---------------------|  
|Crear nuevos controles enlazados a datos.<br /><br /> Enlazar controles existentes a datos.|[Cómo: Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)|  
|Crear controles que muestren los datos relacionados de una relación primaria\-secundaria: cuando el usuario selecciona un registro de datos primario en un control, otro control muestra los datos secundarios relacionados correspondientes al registro seleccionado.|[Cómo: Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Crear una *tabla de búsqueda* que muestre información de una tabla según el valor de un campo de clave externa de otra tabla.|[Cómo: Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Enlazar un control a una imagen de una base de datos.|[Cómo: Enlazar controles a imágenes desde una base de datos](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## Destinos de colocación válidos  
 Los elementos de la ventana **Orígenes de datos** solo se pueden arrastrar hasta destinos de colocación válidos de [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  Principalmente, existen dos tipos de destinos de colocación válidos: contenedores y controles.  Un contenedor es un elemento de la interfaz de usuario que normalmente contiene controles.  Por ejemplo, una cuadrícula es un contenedor, como también lo es una ventana.  
  
## Código y XAML generado  
 Al arrastrar un elemento desde la ventana **Orígenes de datos** hasta [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que define un nuevo control enlazado a datos \(o enlaza un control existente al origen de datos\).  En el caso de algunos orígenes de datos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] también genera código en el archivo de código subyacente que llena de datos el origen de datos.  
  
 En la tabla siguiente se muestra el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] y el código que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera para cada tipo de origen de datos en la ventana **Orígenes de datos**.  
  
|Origen de datos|Genera XAML que enlaza un control al origen de datos|Genera código que llena de datos el origen de datos|  
|---------------------|----------------------------------------------------------|---------------------------------------------------------|  
|Conjunto de datos|Sí|Sí|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Sí|Sí|  
|Servicio|Sí|No|  
|Objeto|Sí|No|  
  
### Conjuntos de datos  
 Cuando se arrastra una tabla o columna desde la ventana **Orígenes de datos** hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que realiza lo siguiente:  
  
-   Agrega el conjunto de datos y un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento.  <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos del conjunto de datos.  
  
-   Crea un enlace de datos para un control.  Si se arrastra el elemento hasta un control existente en el diseñador, el XAML enlaza el control al elemento.  Si se arrastra el elemento hasta un contenedor, el XAML crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento.  El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] también realiza los cambios siguientes en el archivo de código subyacente:  
  
-   Crea un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded> para el elemento de [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contiene el control.  El controlador de eventos llena de datos la tabla, recupera <xref:System.Windows.Data.CollectionViewSource> de los recursos del contenedor y, a continuación, convierte el primer elemento de datos en el elemento actual.  Si ya existe un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded>, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agrega este código al controlador de eventos existente.  
  
### Entity Data Models  
 Al arrastrar una entidad o una propiedad de entidad desde la ventana **Orígenes de datos** hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que realiza lo siguiente:  
  
-   Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento.  <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos de la entidad.  
  
-   Crea un enlace de datos para un control.  Si se arrastra el elemento hasta un control existente en el diseñador, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] enlaza el control al elemento.  Si se arrastra el elemento hasta un contenedor, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento.  El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.  
  
 Visual Studio también realiza los cambios siguientes en el archivo de código subyacente:  
  
-   Agrega un nuevo método que devuelve una consulta para la entidad que se arrastró hasta el diseñador \(o la entidad que contiene la propiedad que se arrastró hasta el diseñador\).  El nuevo método tiene el nombre Get*NombreEntidad*Query, donde *NombreEntidad* es el nombre de la entidad.  
  
-   Crea un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded> para el elemento de [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contiene el control.  El controlador de eventos llama al método Get*NombreEntidad*Query para llenar de datos la entidad, recupera <xref:System.Windows.Data.CollectionViewSource> de los recursos del contenedor y, a continuación, convierte el primer elemento de datos en el elemento actual.  Si ya existe un controlador de eventos <xref:System.Windows.FrameworkElement.Loaded>, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agrega este código al controlador de eventos existente.  
  
### Servicios  
 Cuando se arrastra un objeto o una propiedad de servicio desde la ventana **Orígenes de datos** hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera código [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que crea un control enlazado a datos \(o enlaza un control existente al objeto o la propiedad\).  Sin embargo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no genera código que llene de datos el objeto de servicio del proxy.  Este código se debe escribir expresamente.  Para obtener un ejemplo que muestra cómo hacer esto, consulte [Tutorial: Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 Visual Studio genera XAML que realiza lo siguiente:  
  
-   Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento.  <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos en el objeto devuelto por el servicio.  
  
-   Crea un enlace de datos para un control.  Si se arrastra el elemento hasta un control existente en el diseñador, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] enlaza el control al elemento.  Si se arrastra el elemento hasta un contenedor, el [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento.  El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.  
  
### Objetos  
 Cuando se arrastra un objeto o una propiedad desde la ventana **Orígenes de datos** hasta el diseñador, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera código [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que crea un control enlazado a datos \(o enlaza un control existente al objeto o la propiedad\).  Sin embargo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no genera el código que llena de datos el objeto.  Este código se debe escribir expresamente.  
  
> [!NOTE]
>  Las clases personalizadas deben ser públicas y tener un constructor sin parámetros predeterminado.  No pueden ser clases anidadas que contengan un "punto" en su sintaxis.  Para obtener más información, consulte este artículo sobre las [Clases XAML y personalizadas para WPF](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera un código [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)], que realiza lo siguiente:  
  
-   Agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> a los recursos del contenedor al que se arrastró el elemento.  <xref:System.Windows.Data.CollectionViewSource> es un objeto que se puede usar para navegar y mostrar los datos del objeto.  
  
-   Crea un enlace de datos para un control.  Si se arrastra el elemento hasta un control existente en el diseñador, el XAML enlaza el control al elemento.  Si se arrastra el elemento hasta un contenedor, el XAML crea el control que se seleccionó para el elemento arrastrado y enlaza el control al elemento.  El control se crea dentro de una nueva clase <xref:System.Windows.Controls.Grid>.  
  
## Vea también  
 [Cómo: Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Cómo: Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Cómo: Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Enlazar controles WPF a Entity Data Model](http://msdn.microsoft.com/data/jj574514.aspx)   
 [Tutorial: Enlazar controles WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Tutorial: Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)