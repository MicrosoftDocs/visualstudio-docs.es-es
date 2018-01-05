---
title: "Tutorial: Crear un objeto DataTable en el Diseñador de Dataset | Documentos de Microsoft"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 7df2579f5556e0e35b4203c700ca3f96f46a7d2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Tutorial: Crear un DataTable en el Diseñador de Dataset

En este tutorial se explica cómo crear un <xref:System.Data.DataTable> (sin un TableAdapter) mediante el **Diseñador de Dataset**. Para obtener información sobre cómo crear tablas de datos que incluyen TableAdapters, vea [crear y configurar los TableAdapters](../data-tools/create-and-configure-tableadapters.md).  

Las tareas ilustradas en este tutorial incluyen:  

-   Crear un nuevo proyecto de aplicación de Windows Forms  

-   Agregar un nuevo conjunto de datos a la aplicación  

-   Agregar una nueva tabla de datos al conjunto de datos  

-   Agregar columnas a la tabla de datos  

-   Configuración de la clave principal de la tabla  

## <a name="creating-a-new-windows-forms-application"></a>Crear una nueva aplicación de formularios Windows Forms

### <a name="to-create-a-new-windows-forms-application-project"></a>Para crear un nuevo proyecto de aplicación de Windows Forms  
  
1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .  
  
2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.  

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.  

4. Denomine el proyecto **DataTableWalkthrough**y, a continuación, elija **Aceptar**. 
  
     El **DataTableWalkthrough** proyecto se crea y se agrega a **el Explorador de soluciones**.  

## <a name="adding-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de datos a la aplicación

### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para agregar un nuevo elemento del conjunto de datos al proyecto  
  
1.  En el **proyecto** menú, seleccione **Agregar nuevo elemento...** .  
  
     Aparecerá el cuadro de diálogo Agregar nuevo elemento.  
  
2.  En el panel izquierdo, seleccione **datos**, a continuación, seleccione **conjunto de datos** en el panel central.  
  
3.  Haga clic en **Agregar**.  
  
     Visual Studio agrega un archivo denominado **DataSet1.xsd** al proyecto y lo abre en el **Diseñador de Dataset**.  

## <a name="adding-a-new-datatable-to-the-dataset"></a>Agregar una nueva DataTable al conjunto de datos  

### <a name="to-add-a-new-data-table-to-the-dataset"></a>Para agregar una nueva tabla de datos al conjunto de datos  
  
1.  Arrastre un **DataTable** desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.  
  
     Una tabla denominada **DataTable1** se agrega al conjunto de datos.  
   
2.  Haga clic en la barra de título de **DataTable1** y cambie su nombre `Music`.  

## <a name="adding-columns-to-the-datatable"></a>Agregar columnas a la tabla de datos

### <a name="to-add-columns-to-the-datatable"></a>Para agregar columnas a la tabla de datos  
  
1.  Haga clic en el **música** tabla. Seleccione **agregar**y, a continuación, haga clic en **columna**.  
  
2.  Nombre de la columna `SongID`.  
  
3.  En el **propiedades** ventana, establezca el <xref:System.Data.DataColumn.DataType%2A> propiedad <xref:System.Int16?displayProperty=fullName>.  
  
4.  Repita este proceso y agregue las siguientes columnas:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Configuración de la clave principal de la tabla

Todas las tablas de datos deben tener una clave principal. Una clave principal identifica de forma única un registro específico en una tabla de datos.  
  
### <a name="to-set-the-primary-key-of-the-data-table"></a>Para establecer la clave principal de la tabla de datos
  
-   Haga clic en el **IdCanción** columna y, a continuación, haga clic en **establecer clave principal**.  
  
     Un icono clave aparece junto a la **IdCanción** columna.  
  
## <a name="saving-your-project"></a>Guardar el proyecto  
  
### <a name="to-save-the-datatablewalkthrough-project"></a>Para guardar el proyecto DataTableWalkthrough  
  
-   En el **archivo** menú, haga clic en **guardar todo**.  

## <a name="see-also"></a>Vea también

[Crear y configurar conjuntos de datos en Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
[Validar datos](../data-tools/validate-data-in-datasets.md)  
[Guardar datos](../data-tools/saving-data.md)