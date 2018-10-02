---
title: 'Tutorial: Crear un objeto TableAdapter con varias consultas | Microsoft Docs'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577660"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Tutorial: Crear un objeto TableAdapter con varias consultas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, creará un TableAdapter en un conjunto de datos mediante el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). El tutorial le guiará por el proceso de creación de una segunda consulta en el [TableAdapter](../data-tools/tableadapter-overview.md) utilizando el [editar TableAdapters](../data-tools/editing-tableadapters.md) dentro de la [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo **aplicación Windows** proyecto.  
  
-   Crear y configurar un origen de datos en la aplicación mediante la creación de un conjunto de datos con el **Asistente para configuración de origen de datos**.  
  
-   Abrir el nuevo conjunto de datos en el **Diseñador de Dataset**.  
  
-   Agregar consultas al TableAdapter con el **TableAdapter Query Configuration Wizard**.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind (versión de SQL Server o Access). Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Crear una nueva aplicación para Windows  
 El primer paso consiste en crear una aplicación Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Para crear un proyecto de aplicación para Windows nuevo  
  
1.  En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Elija un lenguaje de programación en el **tipos de proyecto** panel.  
  
3.  Haga clic en **aplicación Windows** en el **plantillas** panel.  
  
4.  Denomine el proyecto `TableAdapterQueriesWalkthrough`y, a continuación, haga clic en **Aceptar**.  
  
     Visual Studio agrega el proyecto al **el Explorador de soluciones** y muestra un formulario nuevo en el diseñador.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Crear un origen de datos de la base de datos con un TableAdapter  
 Este paso crea un origen de datos utilizando el **Asistente para configuración de origen de datos** según el `Customers` tabla en la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En el **elegir la conexión de datos** realice página uno de los siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo.  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.  
  
6.  Haga clic en **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.  
  
7.  Expanda el **tablas** nodo en el **elija los objetos de base de datos** página.  
  
8.  Seleccione el **clientes** de tabla y, a continuación, haga clic en **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y la **clientes** tabla aparece en el **orígenes de datos** ventana.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Abrir el conjunto de datos en el Diseñador de DataSet  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Para abrir el conjunto de datos en el Diseñador de DataSet  
  
1.  Haga clic en **NorthwindDataset** en el **orígenes de datos** ventana.  
  
2.  En el menú contextual, elija **Editar DataSet con el diseñador**.  
  
     NorthwindDataset se abre en el **Diseñador de Dataset**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Agregar una segunda consulta a CustomersTableAdapter  
 El asistente creó el conjunto de datos con un **clientes** tabla de datos y **CustomersTableAdapter**. Esta sección del tutorial agrega una segunda consulta a la **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>Para agregar una segunda consulta a CustomersTableAdapter  
  
1.  Arrastre un **consulta** desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en el **clientes** tabla.  
  
     El [editar TableAdapters](../data-tools/editing-tableadapters.md) se abre.  
  
2.  Seleccione **usar instrucciones SQL**y, a continuación, haga clic en **siguiente**.  
  
3.  Seleccione **LECT que devuelve filas**y, a continuación, haga clic en **siguiente**.  
  
4.  Agregue una cláusula WHERE a la consulta, de forma que se lea:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Si usa la versión de Access de Northwind, reemplace el @City parámetro con un signo de interrogación. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  En el **elija los métodos para generar** página, asigne el nombre del **rellenar un DataTable** método `FillByCity`.  
  
    > [!NOTE]
    >  El método **devolver un DataTable** no se utiliza en este tutorial, por lo que puede desactivar la casilla de verificación o deje el nombre predeterminado.  
  
6.  Haga clic en **siguiente** y finalice el asistente.  
  
     El **FillByCity** consulta se agrega a la **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Agregar código para ejecutar la consulta adicional en el formulario  
  
#### <a name="to-execute-the-query"></a>Para ejecutar la consulta  
  
1.  Seleccione **Form1** en **el Explorador de soluciones**y haga clic en **Diseñador de vistas**.  
  
2.  Arrastre el **clientes** nodo desde el **orígenes de datos** ventana **Form1**.  
  
3.  Cambiar a vista de código seleccionando **código** desde el **vista** menú.  
  
4.  Reemplace el código del controlador de eventos `Form1_Load` por lo siguiente para ejecutar la consulta `FillByCity`.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5.  
  
-   La cuadrícula se rellena con los clientes que tengan el valor `City` en `Seattle`.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
### <a name="to-add-functionality-to-your-application"></a>Para agregar funcionalidad a la aplicación  
  
-   Agregue un control <xref:System.Windows.Forms.TextBox> y un control <xref:System.Windows.Forms.Button> y pase el valor del cuadro de texto a la consulta. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Agregue la lógica de validación al evento <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> de las tablas de datos en el conjunto de datos. Para obtener más información, consulte [validar datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)