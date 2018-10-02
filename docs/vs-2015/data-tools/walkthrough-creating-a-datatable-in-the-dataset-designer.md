---
title: 'Tutorial: Crear un DataTable en el Diseñador de Dataset | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 832dba200fca438d000bae101381389ea20cfb17
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574658"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Tutorial: Crear un DataTable en el Diseñador de Dataset
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se explica cómo crear un <xref:System.Data.DataTable> (sin un TableAdapter) mediante el **Diseñador de Dataset**. Para obtener información sobre la creación de tablas de datos que incluyen los TableAdapters, vea [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto de aplicación de Windows  
  
-   Agregar un nuevo conjunto de datos a la aplicación  
  
-   Agregar una nueva tabla de datos al conjunto de datos  
  
-   Agregar columnas a la tabla de datos  
  
-   Establecer la clave principal de la tabla  
  
## <a name="creating-a-new-windows-application"></a>Crear una nueva aplicación para Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Para crear un proyecto de aplicación para Windows nuevo  
  
1.  Desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Elija un lenguaje de programación en el **tipos de proyecto** panel.  
  
3.  Haga clic en **aplicación Windows** en el **plantillas** panel.  
  
4.  Denomine el proyecto `DataTableWalkthrough`y, a continuación, haga clic en **Aceptar**.  
  
     Visual Studio agrega el proyecto al **el Explorador de soluciones** y muestra **Form1** en el diseñador.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Agregar un nuevo conjunto de datos a la aplicación  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para agregar un nuevo elemento del conjunto de datos al proyecto  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
     Aparece el cuadro de diálogo Agregar nuevo elemento.  
  
2.  En el **plantillas** cuadro, seleccione **DataSet**.  
  
3.  Haga clic en **Agregar**.  
  
     Visual Studio agregará un archivo denominado **DataSet1.xsd** al proyecto y ábralo en el **Diseñador de Dataset**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Agregar una nueva DataTable al conjunto de datos  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Para agregar una nueva tabla de datos al conjunto de datos  
  
1.  Arrastre un **DataTable** desde el **DataSet** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.  
  
     Una tabla denominada **DataTable1** se agrega al conjunto de datos.  
  
    > [!NOTE]
    >  Para crear una tabla de datos que incluya un TableAdapter, vea [Tutorial: crear un objeto TableAdapter con varias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Haga clic en la barra de título de **DataTable1** y cámbiele el nombre `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Agregar columnas a la tabla de datos  
  
#### <a name="to-add-columns-to-the-data-table"></a>Para agregar columnas a la tabla de datos  
  
1.  Haga clic en el **música** tabla. Seleccione **agregar**y, a continuación, haga clic en **columna**.  
  
2.  Nombre de la columna `SongID`.  
  
3.  En el **propiedades** ventana, establezca el <xref:System.Data.DataColumn.DataType%2A> propiedad <xref:System.Int16?displayProperty=fullName>.  
  
4.  Repita este proceso y agregue las siguientes columnas:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Establecer la clave principal de la tabla  
 Todas las tablas de datos deben tener una clave principal. Una clave principal identifica un registro específico en una tabla de datos.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Para establecer la clave principal de la tabla de datos  
  
-   Haga clic en el **IdCanción** columna y, a continuación, haga clic en **establecer clave principal**.  
  
     Un icono clave aparece junto a la **IdCanción** columna.  
  
## <a name="saving-your-project"></a>Guardar el proyecto  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Para guardar el proyecto DataTableWalkthrough  
  
-   En el **archivo** menú, haga clic en **guardar todo**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Ahora que ha creado la tabla, desea realizar una de las acciones siguientes:  
  
|En|Vea|  
|--------|---------|  
|Crear un formulario para los datos de entrada|[Tutorial: Mostrar datos en un formulario Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Agregar datos a la tabla|[Agregar datos a un objeto DataTable](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Ver datos en una tabla|[Visualización de datos en un objeto DataTable](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Editar datos|[Ediciones de DataTable](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Eliminar una fila de una tabla|[Eliminación de DataRow](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Vea también  
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)