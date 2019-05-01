---
title: Enlazar controles WPF a datos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5c1733d6d4e60aad10896dbd2fcad16406830b83
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437040"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Enlace de controles de WPF a datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear enlazados a datos [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] controles mediante el uso de la **orígenes de datos** ventana. En primer lugar, agregue un origen de datos a la **orígenes de datos** ventana. A continuación, arrastre elementos desde el **orígenes de datos** ventana a la**WPF Designer**.

## <a name="adding"></a> Agregar un origen de datos a la ventana de orígenes de datos
 Para poder crear controles enlazados a datos, primero debe agregar un origen de datos a la **orígenes de datos** ventana.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Para agregar un origen de datos a la ventana Orígenes de datos

1. En el **vista** menú, elija **Other Windows**y, a continuación, haga clic en **orígenes de datos**.

2. Haga clic en **Agregar nuevo origen de datos** y complete el **Asistente para configuración de orígenes de datos**.

3. Realice una de las tareas siguientes para crear controles enlazados a datos:

    - [Crear un control enlazado a un único campo de datos](#simple).

    - [Crear un control enlazado a varios campos de datos](#complex).

    - [Crear un conjunto de controles que están enlazados a varios campos de datos](#details).

    - [Enlazar datos a controles existentes en el diseñador](#existing).

## <a name="simple"></a> Crear un control que está enlazado a un único campo de datos
 Después de agregar un origen de datos a la **orígenes de datos** ventana, puede crear un nuevo control enlazado a datos que muestra un único campo de datos, como un <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Para crear un control enlazado a un único campo de datos

1. En el **orígenes de datos** ventana, expanda un elemento que representa una tabla o un objeto. Busque el elemento secundario que represente la columna o propiedad de destino del enlace. Para obtener un ejemplo visual, consulte [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Opcionalmente, seleccione el control que desee crear. Cada elemento de la **orígenes de datos** ventana tiene un control predeterminado que se crea al arrastrar el elemento hasta el diseñador. El control predeterminado depende del tipo de datos subyacente del elemento.

     Para elegir un control diferente, haga clic en la flecha desplegable situada al lado del elemento y seleccione un control. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Arrastre el elemento a un contenedor válido en el diseñador. Para obtener más información acerca de los contenedores válidos, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea el nuevo control enlazado a datos y un título apropiado <xref:System.Windows.Controls.Label> en el contenedor. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] también genera código [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] y código para enlazar el control a los datos. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="complex"></a> Crear un control que está enlazado a varios campos de datos
 Después de agregar un origen de datos a la **orígenes de datos** ventana, puede crear un nuevo control enlazado a datos que muestre varios campos de datos, como un <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Para crear un control enlazado a varios campos de datos

1. En el **orígenes de datos** ventana, seleccione un elemento que representa una tabla u objeto. Para obtener un ejemplo visual, consulte [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Opcionalmente, seleccione el control que desee crear. De forma predeterminada, cada elemento en el **orígenes de datos** ventana que representa una tabla de datos o un objeto se establece para crear un <xref:System.Windows.Controls.DataGrid> (si el proyecto tiene como destino .NET Framework 4) o <xref:System.Windows.Controls.ListView> (para versiones anteriores de .NET Framework).

     Para seleccionar un control diferente, haga clic en la flecha desplegable situada al lado del elemento y seleccione un control. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Si no desea mostrar una columna o propiedad concreta, expanda el elemento para mostrar sus elementos secundarios. Haga clic en la flecha desplegable situada junto a la columna o propiedad que no desea mostrar y, a continuación, haga clic en **ninguno**.

3. Arrastre el elemento hasta un contenedor válido en el diseñador, como <xref:System.Windows.Controls.Grid>. Para obtener más información acerca de los contenedores válidos, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea el nuevo control enlazado a datos en el contenedor. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] también genera código [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] y código para enlazar el control a los datos. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="details"></a> Crear un conjunto de controles que están enlazados a varios campos de datos
 Después de agregar un origen de datos a la **orígenes de datos** ventana, puede enlazar una tabla de datos o un objeto a un conjunto de controles. Se crea un control diferente para cada columna o propiedad de la tabla u objeto.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Para crear un conjunto de controles enlazados a varios campos de datos

1. En el **orígenes de datos** ventana, seleccione un elemento que representa una tabla u objeto. Para obtener un ejemplo visual, consulte [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Haga clic en la flecha desplegable junto al elemento y seleccione **detalles**.

    > [!NOTE]
    > Si no desea mostrar una columna o propiedad concreta, expanda el elemento para mostrar sus elementos secundarios. Haga clic en la flecha desplegable situada junto a la columna o propiedad que no desea mostrar y, a continuación, haga clic en **ninguno**.

3. Arrastre el elemento hasta un contenedor válido en el diseñador, como <xref:System.Windows.Controls.Grid>. Para obtener más información acerca de los contenedores válidos, vea [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea los nuevos controles enlazados a datos en el contenedor. Cada control se enlaza a una columna o propiedad diferente, y está acompañado por un control adecuadamente titulado <xref:System.Windows.Controls.Label>. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] también genera código [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] y código para enlazar los controles a los datos. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="existing"></a> Binddata a controles existentes en el diseñador
 Después de agregar un origen de datos a la **orígenes de datos** ventana, puede agregar un enlace a un control existente en el Diseñador de datos.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Para enlazar los datos a un control existente en el diseñador

1. En el **orígenes de datos** ventana, use uno de los siguientes procedimientos:

    - Para agregar un enlace de datos a un control existente que muestra varios campos de datos, como <xref:System.Windows.Controls.DataGrid> o <xref:System.Windows.Controls.ListView>, seleccione el elemento que representa la tabla u objeto que desea enlazar al control.

    - Para agregar un enlace de datos a un control existente que muestra un único campo de datos, como <xref:System.Windows.Controls.ComboBox> o <xref:System.Windows.Controls.TextBox>, expanda el elemento que representa la tabla u objeto que contiene los datos y, a continuación, seleccione el elemento que representa los datos que desea enlazar al control.

2. Arrastre el elemento seleccionado de la **orígenes de datos** ventana a un control existente en el diseñador. El control debe ser un destino de colocación válido. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] y código para enlazar el control a los datos. Para obtener más información, consulte [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Si el control ya está enlazado a datos, el enlace de datos del control se restablece en el elemento que se arrastró hasta el control en último término.

## <a name="see-also"></a>Vea también
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [crear tablas de búsqueda en aplicaciones WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [mostrar datos relacionados en aplicaciones WPF](../data-tools/display-related-data-in-wpf-applications.md) [WPF enlazar controles a un conjunto de datos](../data-tools/bind-wpf-controls-to-a-dataset.md) [WPF enlazar controles a un servicio de datos WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Tutorial: Mostrar datos relacionados en una aplicación WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
