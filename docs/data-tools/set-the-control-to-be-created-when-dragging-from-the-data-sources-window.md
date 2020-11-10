---
title: Establecer el control que se va a crear al arrastrar
description: Descubra cómo establecer el control que se creará al arrastrar desde la ventana orígenes de datos hasta WPF Designer o el diseñador de Windows Forms en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8a81ecb35c37dbef6d48227c27ed877c64e6e26f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434472"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos

Puede crear controles enlazados a datos si arrastra los elementos desde la ventana **Orígenes de datos** hasta WPF Designer o el Diseñador de Windows Forms. Cada elemento de la ventana **Orígenes de datos** tiene un control predeterminado que se crea al arrastrar el elemento hacia el diseñador. Sin embargo, puede elegir crear un control diferente.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Establecimiento de los controles que se van a crear para tablas de datos u objetos

Antes de arrastrar los elementos que representan objetos o tablas de datos a la ventana **Orígenes de datos** , puede decidir mostrar todos los datos en un control o mostrar cada columna o propiedad en un control independiente.

En este contexto, el término *objeto* hace referencia a un objeto comercial personalizado, una entidad (en un Entity Data Model) o un objeto devuelto por un servicio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Para establecer los controles que se van a crear para tablas de datos u objetos

1. Asegúrese de que **WPF** Designer o el diseñador de **Windows Forms** está abierto.

2. En la ventana **Orígenes de datos** , seleccione el elemento que representa el objeto o la tabla de datos que desea establecer.

   > [!TIP]
   > Si la ventana **orígenes de datos** no está abierta, puede abrirla seleccionando **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

3. Haga clic en el menú desplegable del elemento y, a continuación, en uno de los siguientes elementos en el menú:

    - Para mostrar cada campo de datos en un control independiente, haga clic en **Detalles**. Al arrastrar el elemento de datos hacia el diseñador, se creará un control enlazado a datos diferente por cada columna o propiedad del objeto o tabla de datos primaria, junto con las etiquetas de cada control.

    - Para mostrar todos los datos en un control único, seleccione un control diferente de la lista, como **DataGrid** o **List** en una aplicación WPF o **DataGridView** en una aplicación de Windows Forms.

    La lista de controles disponibles depende del diseñador que tenga abierto, la versión de .NET a la que se destina el proyecto y de si ha agregado controles personalizados que admiten el enlace de datos al **cuadro de herramientas**. Si el control que desea crear no está en la lista de controles disponibles, puede Agregar el control a la lista. Para obtener más información, vea [Agregar controles personalizados a la ventana orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Para obtener información sobre cómo crear un control de Windows Forms personalizado que se pueda agregar a la lista de controles de tablas de datos u objetos de la ventana **orígenes de datos** , vea [crear un control de usuario Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Establecer los controles que se van a crear para las columnas de datos o propiedades

Antes de arrastrar al diseñador un elemento que representa una columna o la propiedad de un objeto en la ventana **Orígenes de datos** , puede establecer el control que se va a crear.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Para establecer los controles que se van a crear para columnas o propiedades

1. Asegúrese de que **WPF** Designer o el diseñador de **Windows Forms** está abierto.

2. En la ventana **Orígenes de datos** , expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.

3. Seleccione cada columna o propiedad para la que desea establecer el control que se va a crear.

4. Haga clic en el menú desplegable de la columna o propiedad y seleccione el control que desea crear cuando el elemento se arrastre al diseñador.

     La lista de controles disponibles depende del diseñador que se haya abierto, la versión de .NET a la que se destina el proyecto y los controles personalizados que admiten el enlace de datos que se ha agregado al **cuadro de herramientas**. Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista. Para obtener más información, vea [Agregar controles personalizados a la ventana orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Para obtener información sobre cómo crear un control personalizado que se pueda agregar a la lista de controles para columnas de datos o propiedades en la ventana **orígenes de datos** , vea [crear un Windows Forms control de usuario que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Si no desea crear un control para la columna o propiedad, seleccione **ninguno** en el menú desplegable. Esto es útil si desea arrastrar la tabla o el objeto principal al diseñador, pero sin incluir la columna o propiedad concreta.

## <a name="see-also"></a>Consulte también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
