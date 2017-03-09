---
title: "C&#243;mo: Enlazar controles WPF a datos en Visual Studio | Microsoft Docs"
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
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Enlazar controles WPF a datos en Visual Studio
Puede crear controles de [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] enlazados a datos en la ventana **Orígenes de datos**.  En primer lugar, agregue un origen de datos a la ventana **Orígenes de datos**.  A continuación, arrastre los elementos a **WPF Designer** desde la ventana **Orígenes de datos**.  
  
##  <a name="adding"></a> Agregar un origen de datos a la ventana Orígenes de datos  
 Antes de crear controles enlazados a datos, debe agregar un origen de datos a la ventana **Orígenes de datos**.  
  
#### Para agregar un origen de datos a la ventana Orígenes de datos  
  
1.  En el menú **Ver**, elija **Otras ventanas** y, a continuación, haga clic en **Orígenes de datos**.  
  
2.  Haga clic en **Agregar nuevo origen de datos** y complete el **Asistente para configuración de orígenes de datos**.  
  
3.  Realice una de las tareas siguientes para crear controles enlazados a datos:  
  
    -   [Crear un control enlazado a un único campo de datos](#simple).  
  
    -   [Crear un control enlazado a varios campos de datos](#complex).  
  
    -   [Crear un conjunto de controles enlazados a varios campos de datos](#details).  
  
    -   [Enlazar datos a controles existentes en el diseñador](#existing).  
  
##  <a name="simple"></a> Crear un control enlazado a un único campo de datos  
 Después de agregar un origen de datos a la ventana **Orígenes de datos**, puede crear un nuevo control enlazado a datos que muestre un único campo de datos, como <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>.  
  
#### Para crear un control enlazado a un único campo de datos  
  
1.  En la ventana **Orígenes de datos**, expanda un elemento que represente una tabla o un objeto.  Busque el elemento secundario que represente la columna o propiedad de destino del enlace.  Dispone de un ejemplo visual en [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Opcionalmente, seleccione el control que desee crear.  Cada elemento de la ventana **Orígenes de datos** tiene un control predeterminado que se crea al arrastrar el elemento hacia el diseñador.  El control predeterminado depende del tipo de datos subyacente del elemento.  
  
     Para elegir un control diferente, haga clic en la flecha desplegable situada al lado del elemento y seleccione un control.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Arrastre el elemento hasta un contenedor válido en el diseñador, como <xref:System.Windows.Controls.Grid>.  Para obtener más información acerca de los contenedores válidos, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea el nuevo control enlazado a datos así como un control <xref:System.Windows.Controls.Label> con un título apropiado en el contenedor.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] también genera código [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] y código para enlazar el control a los datos.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="complex"></a> Crear un control enlazado a varios campos de datos  
 Después de agregar un origen de datos a la ventana **Orígenes de datos**, puede crear un nuevo control enlazado a datos que muestre varios campos de datos, como <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>.  
  
#### Para crear un control enlazado a varios campos de datos  
  
1.  En la ventana **Orígenes de datos**, seleccione un elemento que represente una tabla o un objeto.  Dispone de un ejemplo visual en [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Opcionalmente, seleccione el control que desee crear.  De forma predeterminada, cada elemento de la ventana **Orígenes de datos** que representa una tabla u objeto de datos se establece para crear <xref:System.Windows.Controls.DataGrid> \(si su proyecto está orientado a .NET Framework 4\) o <xref:System.Windows.Controls.ListView> \(para versiones anteriores de .NET Framework\).  
  
     Para seleccionar un control diferente, haga clic en la flecha desplegable situada al lado del elemento y seleccione un control.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si no desea mostrar una columna o propiedad concreta, expanda el elemento para mostrar sus elementos secundarios.  Haga clic en la flecha desplegable situada al lado de la columna o propiedad que no desea mostrar y, a continuación, haga clic en **Ninguno**.  
  
3.  Arrastre el elemento hasta un contenedor válido en el diseñador, como <xref:System.Windows.Controls.Grid>.  Para obtener más información acerca de los contenedores válidos, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea el nuevo control enlazado a datos en el contenedor. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera también [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] y código para enlazar el control a los datos.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="details"></a> Crear un conjunto de controles enlazados a varios campos de datos  
 Después de agregar un origen de datos a la ventana **Orígenes de datos**, puede enlazar una tabla u objeto de datos a un conjunto de controles.  Se crea un control diferente para cada columna o propiedad de la tabla u objeto.  
  
#### Para crear un conjunto de controles enlazados a varios campos de datos  
  
1.  En la ventana **Orígenes de datos**, seleccione un elemento que represente una tabla o un objeto.  Dispone de un ejemplo visual en [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
2.  Haga clic en la flecha desplegable situada al lado del elemento y seleccione **Detalles**.  
  
    > [!NOTE]
    >  Si no desea mostrar una columna o propiedad concreta, expanda el elemento para mostrar sus elementos secundarios.  Haga clic en la flecha desplegable situada al lado de la columna o propiedad que no desea mostrar y, a continuación, haga clic en **Ninguno**.  
  
3.  Arrastre el elemento hasta un contenedor válido en el diseñador, como <xref:System.Windows.Controls.Grid>.  Para obtener más información acerca de los contenedores válidos, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea los nuevos controles enlazados a datos en el contenedor.  Cada control se enlaza a una columna o propiedad diferente, y está acompañado por un control adecuadamente titulado<xref:System.Windows.Controls.Label>. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera también [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] y código para enlazar los controles a los datos.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="existing"></a> Enlazar datos a controles existentes en el diseñador  
 Después de agregar un origen de datos a la ventana **Orígenes de datos**, puede agregar un enlace de datos a un control existente en el diseñador.  
  
#### Para enlazar los datos a un control existente en el diseñador  
  
1.  En la ventana **Orígenes de datos**, use uno de los procedimientos siguientes:  
  
    -   Para agregar un enlace de datos a un control existente que muestra varios campos de datos, como <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>, seleccione el elemento que representa la tabla u objeto que desea enlazar al control.  
  
    -   Para agregar un enlace de datos a un control existente que muestra un único campo de datos, como <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>, expanda el elemento que representa la tabla u objeto que contiene los datos y, a continuación, seleccione el elemento que representa los datos que desea enlazar al control.  
  
2.  Arrastre el elemento seleccionado desde la ventana **Orígenes de datos** hasta un control existente en el diseñador.  El control debe ser un destino de colocación válido.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] y código para enlazar el control a los datos.  Para obtener más información, vea [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
    > [!NOTE]
    >  Si el control ya está enlazado a datos, el enlace de datos del control se restablece en el elemento que se arrastró hasta el control en último término.  
  
## Vea también  
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Cómo: Crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Cómo: Mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Tutorial: Enlazar controles WPF a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Tutorial: Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)