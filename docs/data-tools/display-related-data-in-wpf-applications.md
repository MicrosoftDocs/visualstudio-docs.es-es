---
title: "C&#243;mo: Mostrar datos relacionados en aplicaciones WPF | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Mostrar datos relacionados en aplicaciones WPF
Es posible que en algunas aplicaciones desee trabajar con datos que procedan de varias tablas o entidades relacionadas entre sí con un tipo de relación primaria\-secundaria.  Por ejemplo, podría desear mostrar una cuadrícula que presentase los clientes de una tabla `Customers`.  Cuando el usuario selecciona un cliente concreto, se muestran en otra cuadrícula los pedidos del cliente de una tabla `Orders` relacionada.  
  
 Puede crear controles enlazados a datos que muestren datos relacionados si arrastra los elementos desde la ventana **Orígenes de datos** hasta WPF Designer.  
  
### Para crear controles que muestren los registros relacionados  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos** para abrir la ventana **Orígenes de datos**.  
  
2.  Haga clic en **Agregar nuevo origen de datos** y complete el **Asistente para configuración de orígenes de datos**.  
  
3.  Abra WPF Designer y asegúrese de que el diseñador tenga un contenedor que sea un destino de colocación válido para los elementos de la ventana **Orígenes de datos**.  
  
     Para obtener más información acerca de los destinos de colocación válidos, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  En la ventana **Orígenes de datos**, expanda el nodo que representa la tabla u objeto primario de la relación.  La tabla u objeto primario está en el lado "uno" de una relación uno a varios.  
  
5.  Arrastre el nodo primario \(o cualquier elemento individual de dicho nodo\) desde la ventana **Orígenes de datos** hasta un destino de colocación válido en el diseñador.  
  
     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada elemento arrastrado.  El XAML también agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> para la tabla u objeto primario a los recursos del destino de colocación.  En el caso de algunos orígenes de datos, Visual Studio genera también código que carga los datos en la tabla u objeto primario.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  En la ventana **Orígenes de datos**, localice la tabla u objeto secundario relacionado.  Las tablas y objetos secundarios relacionados aparecen como nodos expansibles en la parte inferior de la lista de datos del nodo primario.  
  
7.  Arrastre el nodo secundario \(o cualquier elemento individual de dicho nodo\) desde la ventana **Orígenes de datos** hasta un destino de colocación válido en el diseñador.  
  
     Visual Studio genera XAML que crea nuevos controles enlazados a datos para cada uno de los elementos arrastrados.  El XAML también agrega un nuevo objeto <xref:System.Windows.Data.CollectionViewSource> para la tabla u objeto secundario a los recursos del destino de colocación.  Este nuevo objeto <xref:System.Windows.Data.CollectionViewSource> se enlaza a la propiedad de la tabla u objeto primario que acaba de arrastrar al diseñador.  En el caso de algunos orígenes de datos, Visual Studio genera también código que carga los datos en la tabla u objeto secundario.  
  
     En la ilustración siguiente se muestra la tabla **Orders** relacionada de la tabla **Customers** en un conjunto de datos de la ventana **Orígenes de datos**.  
  
     ![Ventana Orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif "DataSources2")  
  
## Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Cómo: Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Cómo: Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)