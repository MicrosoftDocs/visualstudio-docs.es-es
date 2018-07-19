---
title: Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a72800cda8b80daec1adeb82d7884789cc4d2bd7
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174187"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos
Puede crear controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta WPF designer o el Diseñador de Windows Forms. Cada elemento de la **orígenes de datos** ventana tiene un control predeterminado que se crea al arrastrar al diseñador. Sin embargo, puede elegir crear un control diferente.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Establecer los controles que deben crearse para las tablas de datos u objetos
Antes de arrastrar los elementos que representan objetos o tablas de datos de la **orígenes de datos** ventana, puede elegir mostrar todos los datos en un control, o para mostrar cada columna o propiedad en un control independiente.

En este contexto, el término *objeto* hace referencia a un objeto comercial personalizado, una entidad (en un Entity Data Model) o un objeto devuelto por un servicio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Para establecer los controles que se van a crear para tablas de datos u objetos

1.  Asegúrese del **WPF** diseñador o el **Windows Forms** diseñador está abierto.

2.  En el **orígenes de datos** ventana, seleccione el elemento que representa la tabla de datos u objeto que desea establecer.

3.  Haga clic en el menú desplegable del elemento y, a continuación, en uno de los siguientes elementos en el menú:

    -   Para mostrar cada campo de datos en un control independiente, haga clic en **detalles**. Al arrastrar el elemento de datos hacia el diseñador, se creará un control enlazado a datos diferente por cada columna o propiedad del objeto o tabla de datos primaria, junto con las etiquetas de cada control.

    -   Para mostrar todos los datos en un solo control, seleccione un control diferente en la lista, como **DataGrid** o **lista** en una aplicación de WPF o **DataGridView** en un formulario Windows Forms aplicación.

    La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET Framework su proyecto tiene como destino, y si han agregado controles personalizados que compatibilidad con enlaces de datos a la **cuadro de herramientas**. Si el control que desea crear no está en la lista de controles disponibles, puede agregar el control a la lista. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Para obtener información sobre cómo crear un control personalizado de Windows Forms que se puede agregar a la lista de controles para las tablas de datos u objetos en el **orígenes de datos** ventana, consulte [crear un control de usuario de Windows Forms que admita datos complejos enlace](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Establecer los controles que deben crearse para las propiedades o columnas de datos
Antes de arrastrar un elemento que representa una columna o una propiedad de un objeto desde el **orígenes de datos** ventana al diseñador, puede establecer el control que se creará.

#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Para establecer los controles que se van a crear para columnas o propiedades

1.  Asegúrese del **WPF** diseñador o el **Windows Forms** diseñador está abierto.

2.  En el **orígenes de datos** ventana, expanda la tabla deseada o para mostrar sus columnas o propiedades de objeto.

3.  Seleccione cada columna o propiedad para la que desea establecer el control que se va a crear.

4.  Haga clic en el menú desplegable de la columna o propiedad y seleccione el control que desea crear cuando el elemento se arrastre al diseñador.

     La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET Framework su proyecto tiene como destino, y qué controles personalizados que admiten enlace de datos se han agregado a la **cuadro de herramientas**. Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Para obtener información sobre cómo crear un control personalizado que se puede agregar a la lista de controles para columnas de datos o propiedades en el **orígenes de datos** ventana, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Si no desea crear un control para la columna o propiedad, seleccione **ninguno** en el menú desplegable. Esto es útil si desea arrastrar la tabla o el objeto principal al diseñador, pero sin incluir la columna o propiedad concreta.

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)