---
title: Crear un DataTable en el Diseñador de DataSet
description: En este tutorial, cree un objeto DataTable (sin TableAdapter) mediante el Diseñador de DataSet. Cree una nueva aplicación de Windows Forms y agréguele un nuevo conjunto de nuevos.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a0dad1e6878adc73a08753dca21500499e652602
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998257"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Tutorial: crear un DataTable en el Diseñador de DataSet

En este tutorial se explica cómo crear un <xref:System.Data.DataTable> (sin un TableAdapter) mediante el **Diseñador de DataSet**. Para obtener información sobre cómo crear tablas de datos que incluyen TableAdapters, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Crear una nueva aplicación de Windows Forms

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **DataTableWalkthrough** y, a continuación, elija **Aceptar**.

     El proyecto **DataTableWalkthrough** se crea y se agrega a **Explorador de soluciones**.

## <a name="add-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de nuevos a la aplicación

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento** .

2. En el panel izquierdo, seleccione datos y, a continuación, seleccione **conjunto** de **datos** en el panel central.

3. Haga clic en **Agregar**.

     Visual Studio agrega un archivo denominado **DataSet1. xsd** al proyecto y lo abre en el **Diseñador de DataSet**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Agregar un nuevo DataTable al conjunto de

1. Arrastre un **objeto DataTable** desde la pestaña **DataSet** del **cuadro de herramientas** hasta el **Diseñador de DataSet**.

     Se agrega una tabla denominada **DataTable1** al conjunto de DataSet.

2. Haga clic en la barra de título de **DataTable1** y cambie su nombre `Music` .

## <a name="add-columns-to-the-datatable"></a>Agregar columnas a la DataTable

1. Haga clic con el botón secundario en la tabla **música** . Seleccione **Agregar** y, a continuación, haga clic en **Columna**.

2. Asigne un nombre a la columna `SongID` .

3. En la ventana **Propiedades** , establezca la propiedad <xref:System.Data.DataColumn.DataType%2A> en <xref:System.Int16?displayProperty=fullName>.

4. Repita este proceso y agregue las columnas siguientes:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Establecer la clave principal de la tabla

Todas las tablas de datos deben tener una clave principal. Una clave principal identifica de forma única un registro específico en una tabla de datos.

Para establecer la clave principal, haga clic con el botón secundario en la columna **SongID** y, a continuación, haga clic en **establecer clave principal**. Aparece un icono de llave junto a la columna **SongID** .

## <a name="save-your-project"></a>Guardar el proyecto

Para guardar el proyecto **DataTableWalkthrough** , en el menú **archivo** , seleccione **guardar todo**.

## <a name="see-also"></a>Vea también

- [Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validar datos](../data-tools/validate-data-in-datasets.md)
