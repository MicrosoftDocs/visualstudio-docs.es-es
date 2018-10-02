---
title: 'Tutorial: Mostrar datos en un formulario de Windows | Microsoft Docs'
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3decf0da6dd6d16c0128fdaeedf2fcd0cea94871
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579728"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>Tutorial: Mostrar datos en Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno de los escenarios más habituales en el desarrollo de aplicaciones es mostrar datos en un formulario de una aplicación basada en Windows. Puede mostrar datos en un formulario arrastrando elementos desde la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) hasta el formulario. Este tutorial crea un formulario simple que muestra los datos de una tabla única en varios controles individuales. En este ejemplo se utiliza la tabla `Customers` de la base de datos de ejemplo Northwind.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo **aplicación Windows** proyecto.  
  
-   Crear y configurar un conjunto de datos con el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Selecciona el control que se creará en el formulario al arrastrar elementos desde el **orígenes de datos** ventana. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creación de un control enlazado a datos arrastrando elementos desde la **orígenes de datos** ventana hasta su formulario.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind. Para obtener más información, consulte [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-the-windows-application"></a>Crear la aplicación para Windows  
 El primer paso es crear un **aplicación Windows** proyecto.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Para crear el nuevo proyecto de aplicación para Windows  
  
1.  Desde el **archivo** menú, cree un nuevo proyecto.  
  
2.  Dé un nombre al proyecto `DisplayingDataonaWindowsForm`.  
  
3.  Seleccione **aplicación Windows** y haga clic en **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     El **DisplayingDataonaWindowsForm** se crea y se agrega al proyecto **el Explorador de soluciones**.  
  
## <a name="creating-the-data-source"></a>Crear el origen de datos  
 Este paso crea un origen de datos utilizando el **Asistente para configuración de origen de datos** según el `Customers` tabla en la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1.  En el menú **Datos** , haga clic en **Mostrar orígenes de datos**.  
  
2.  En el **orígenes de datos** ventana, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En el **elegir la conexión de datos** realice página uno de los siguientes:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **nueva conexión** para iniciar el **agregar o modificar conexión** cuadro de diálogo...  
  
5.  Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, haga clic en **siguiente**.  
  
6.  Haga clic en **siguiente** en el **Guardar cadena de conexión en el archivo de configuración de la aplicación** página.  
  
7.  Expanda el **tablas** nodo en el **elija los objetos de base de datos** página.  
  
8.  Seleccione el **clientes** de tabla y, a continuación, haga clic en **finalizar**.  
  
     El **NorthwindDataSet** se agrega al proyecto y la **clientes** tabla aparece en el **orígenes de datos** ventana.  
  
## <a name="setting-the-controls-to-be-created"></a>Establecer los controles que se van a crear  
 En este tutorial, los datos estarán en un **detalles** diseño donde se muestran los datos en controles individuales. (El enfoque alternativo es el valor predeterminado **cuadrícula** diseño donde se muestran los datos en un <xref:System.Windows.Forms.DataGridView> control.)  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Para establecer el tipo de acción de colocación de los elementos de la ventana Orígenes de datos  
  
1.  Expanda el **clientes** nodo en el **orígenes de datos** ventana.  
  
2.  Cambiar el tipo de colocación de la **clientes** la tabla a **detalles** seleccionando **detalles** en la lista desplegable de la **clientes** nodo. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Cambiar el **CustomerID** tipo de colocación de la columna a una etiqueta seleccionando **etiqueta** en la lista de control de la **CustomerID** nodo.  
  
## <a name="creating-the-form"></a>Crear el formulario  
 Crear los controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana hasta su formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario  
  
-   Arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
## <a name="testing-the-application"></a>Probar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
-   Presione F5.  
  
-   Navegue por los registros utilizando el control <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que pueden realizarse después de crear un Windows Form enlazado a datos. Entre las mejoras que podría realizar se incluyen:  
  
-   Agregar funcionalidad de búsqueda al formulario. Para obtener más información, consulte [Cómo: agregar una consulta parametrizada a una aplicación de Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Agregar funcionalidad para devolver actualizaciones a la base de datos. Para obtener más información, consulte [Tutorial: guardar datos en una base de datos (tabla única)](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d).  
  
-   Agregar el `Orders` tabla al conjunto de datos seleccionando **configurar DataSet con el asistente** desde el **orígenes de datos** ventana. A continuación, puede agregar controles que muestren los datos relacionados arrastrando el **pedidos** nodo (situado debajo el **Fax** columna dentro de la **clientes** tabla) hasta el formulario. Para más información, consulte [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Introducción a TableAdapter](../data-tools/tableadapter-overview.md)