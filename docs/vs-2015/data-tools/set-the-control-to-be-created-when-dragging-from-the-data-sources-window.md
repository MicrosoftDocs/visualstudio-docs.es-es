---
title: Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos | Microsoft Docs
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
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c9902080ae501c1d77a59f152d7d272462d2264
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563225"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear controles enlazados a datos si arrastra los elementos desde la ventana **Orígenes de datos** hasta WPF Designer o el Diseñador de Windows Forms. Cada elemento de la ventana **Orígenes de datos** tiene un control predeterminado que se crea al arrastrar el elemento hacia el diseñador. Sin embargo, puede elegir crear un control diferente.  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Establecimiento de los controles que se van a crear para tablas de datos u objetos  
 Antes de arrastrar los elementos que representan objetos o tablas de datos a la ventana **Orígenes de datos**, puede decidir mostrar todos los datos en un control o mostrar cada columna o propiedad en un control independiente.  
  
 En este contexto, el término *objeto* hace referencia a un objeto comercial personalizado, una entidad (en un Entity Data Model) o un objeto devuelto por un servicio.  
  
#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Para establecer los controles que se van a crear para tablas de datos u objetos  
  
1. Asegúrese de que el Diseñador de Windows Forms o de WPF está abierto.  
  
2. En la ventana **Orígenes de datos**, seleccione el elemento que representa el objeto o la tabla de datos que desea establecer.  
  
3. Haga clic en el menú desplegable del elemento y, a continuación, en uno de los siguientes elementos en el menú:  
  
   - Para mostrar cada campo de datos en un control independiente, haga clic en **Detalles**. Al arrastrar el elemento de datos hacia el diseñador, se creará un control enlazado a datos diferente por cada columna o propiedad del objeto o tabla de datos primaria, junto con las etiquetas de cada control.  
  
   - Para mostrar todos los datos en un control único, seleccione un control diferente de la lista, como **DataGrid** o **List** en una aplicación WPF o **DataGridView** en una aplicación de Windows Forms.  
  
     La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET Framework sea el destino del proyecto y si se han agregado controles personalizados que admiten el enlace de datos al **Cuadro de herramientas**. Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para obtener información sobre cómo crear un control personalizado de Windows Forms que se puede agregar a la lista de controles para las tablas de datos u objetos en el **orígenes de datos** ventana, consulte [crear un control de usuario de Windows Forms que admita datos complejos enlace](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Establecer los controles que deben crearse para las propiedades o columnas de datos  
 Antes de arrastrar al diseñador un elemento que representa una columna o la propiedad de un objeto en la ventana **Orígenes de datos**, puede establecer el control que se va a crear.  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Para establecer los controles que se van a crear para columnas o propiedades  
  
1. Asegúrese de que el Diseñador de Windows Forms o de WPF está abierto.  
  
2. En la ventana **Orígenes de datos**, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.  
  
3. Seleccione cada columna o propiedad para la que desea establecer el control que se va a crear.  
  
4. Haga clic en el menú desplegable de la columna o propiedad y seleccione el control que desea crear cuando el elemento se arrastre al diseñador.  
  
     La lista de controles disponibles depende de qué diseñador esté abierto, qué versión de .NET Framework sea el destino del proyecto y qué controles personalizados que admiten el enlace de datos se hayan agregado al **Cuadro de herramientas**. Si el control que desea crear está en la lista de controles disponibles, puede agregarlo a la lista. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para obtener información sobre cómo crear un control personalizado que se puede agregar a la lista de controles para columnas de datos o propiedades en el **orígenes de datos** ventana, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Si no desea crear un control para la columna o propiedad, seleccione **ninguno** en el menú desplegable. Esto es útil si desea arrastrar la tabla o el objeto principal al diseñador, pero sin incluir la columna o propiedad concreta.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
