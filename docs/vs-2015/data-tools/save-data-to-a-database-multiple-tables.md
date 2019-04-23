---
title: Guardar datos en una base de datos (varias tablas) | Documentos de Microsoft
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd19af4bc2533d2bd4e7c21dd49eae53510ae429
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118219"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Guardar datos en una base de datos (varias tablas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno de los escenarios más comunes en el desarrollo de aplicaciones consiste en mostrar los datos en un formulario de una aplicación Windows, editar los datos y devolverlos actualizados a la base de datos. Este tutorial crea un formulario en el que aparecen datos de dos tablas relacionadas y muestra cómo editar los registros y volver a guardar los cambios en la base de datos. En este ejemplo se utilizan las tablas `Customers` y `Orders` de la base de datos de ejemplo Northwind.  
  
 Puede guardar los datos de su aplicación en la base de datos llamando al método `Update` de un TableAdapter. Al arrastrar las tablas de la **orígenes de datos** ventana en un formulario, el código necesario para guardar los datos se agrega automáticamente. Cualquier tabla adicional que se agrega a un formulario requiere la adición manual de este código. Este tutorial muestra cómo agregar código para guardar las actualizaciones de varias tablas.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la ayuda según la configuración activa o la edición que esté usando. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
- Crear un nuevo **aplicación Windows** proyecto.  
  
- Crear y configurar un origen de datos en la aplicación con el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Establecer los controles de los elementos de la [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
- Crear controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.  
  
- Modificación de algunos registros de cada tabla en el conjunto de datos.  
  
- Modificar el código para devolver los datos actualizados del conjunto de datos a la base de datos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
- Acceso a la base de datos de ejemplo Northwind.
  
## <a name="create-the-windows-application"></a>Crear la aplicación de Windows  
 El primer paso es crear un **aplicación Windows**. Asignar un nombre al proyecto es opcional durante este paso, pero se lo entregaremos un nombre porque estamos planeando guardarlo más adelante.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Para crear el nuevo proyecto de aplicación de Windows  
  
1. En el **archivo** menú, cree un nuevo proyecto.  
  
2. Dé un nombre al proyecto `UpdateMultipleTablesWalkthrough`.  
  
3. Seleccione **aplicación Windows**y, a continuación, seleccione **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Se crea el proyecto **UpdateMultipleTablesWalkthrough** y se agrega al **Explorador de soluciones**.  
  
## <a name="create-the-data-source"></a>Crear el origen de datos  
 Este paso crea un origen de datos a partir de la base de datos Northwind utilizando el **Asistente para la configuración de orígenes de datos**. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1. En el **datos** menú, seleccione**Mostrar orígenes de datos**.  
  
2. En el **orígenes de datos** ventana, seleccione**Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.  
  
3. En el **elegir un tipo de origen de datos**pantalla, seleccione **base de datos**y, a continuación, seleccione **siguiente**.  
  
4. En el **elegir la conexión de datos**realice pantalla uno de los siguientes:  
  
    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         -o bien-  
  
    - Seleccione **Nueva conexión** para abrir el cuadro de diálogo **Agregar o modificar conexión**.  
  
5. Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione **siguiente**.  
  
6. En el **Guardar cadena de conexión en el archivo de configuración de la aplicación**, seleccione **siguiente**.  
  
7. En el **elija los objetos de base de datos**pantalla, expanda el **tablas** nodo.  
  
8. Seleccione el **clientes** y **pedidos** tablas y, a continuación, seleccione **finalizar**.  
  
     Se agrega **NorthwindDataSet** al proyecto y las tablas aparecen en la ventana **Orígenes de datos**.  
  
## <a name="set-the-controls-to-be-created"></a>Establecer los controles que se puede crear  
 En este tutorial, los datos en el `Customers` la tabla está en un **detalles** diseño donde se muestran los datos en controles individuales. Los datos de la `Orders` la tabla está en un **cuadrícula** diseño que se muestra en un <xref:System.Windows.Forms.DataGridView> control.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Para establecer el tipo de acción de colocación de los elementos de la ventana Orígenes de datos  
  
1. En el **orígenes de datos** ventana, expanda el **clientes** nodo.  
  
2. En el **clientes** nodo, seleccione **detalles** en la lista de control para cambiar el control de la **clientes** tabla a controles individuales. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Crear el formulario enlazado a datos  
 Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para crear controles enlazados en el formulario  
  
1. Arrastre el nodo principal **Customers** desde la ventana **Orígenes de datos** hasta **Form1**.  
  
     Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
2. Arrastre el nodo **Orders** relacionado desde la ventana **Orígenes de datos** hasta **Form1**.  
  
    > [!NOTE]
    >  El nodo **Orders** relacionado se encuentra debajo de la columna **Fax** y es un nodo secundario del nodo **Customers**.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un OrdersTableAdapter y <xref:System.Windows.Forms.BindingSource> aparecen en la Bandeja de componentes.  
  
## <a name="addcode-to-update-the-database"></a>Addcode para actualizar la base de datos  
 Puede actualizar la base de datos llamando a los métodos `Update` de los TableAdapters **Customers** y **Orders**. De forma predeterminada, un controlador de eventos para el **guardar** botón de la<xref:System.Windows.Forms.BindingNavigator> se agrega al código del formulario para enviar actualizaciones a la base de datos. Este procedimiento modifica el código para enviar las actualizaciones en el orden correcto. Esto elimina la posibilidad de generar errores de integridad referencial. El código también implementa el control de errores colocando la llamada de actualización en un bloque try-catch. Puede modificar el código para satisfacer las necesidades de la aplicación.  
  
> [!NOTE]
>  Para mayor claridad, este tutorial no utiliza una transacción. Sin embargo, si va a actualizar dos o más tablas relacionadas, incluir toda la lógica de actualización dentro de una transacción. Una transacción es un proceso que asegura que todos los cambios relacionados en una base de datos sean correctos antes de confirmados los cambios. Para obtener más información, consulte [transacciones y simultaneidad](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Para agregar la lógica de actualización a la aplicación  
  
1. Seleccione el **guardar** situado en la <xref:System.Windows.Forms.BindingNavigator>. Se abrirá el Editor de código para el `bindingNavigatorSaveItem_Click` controlador de eventos.  
  
2. Reemplace el código del controlador de eventos para que llame a los métodos `Update` de los TableAdapters relacionados. El código siguiente crea en primer lugar tres tablas de datos temporales para la información actualizada de cada <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> y <xref:System.Data.DataRowState>). A continuación, las actualizaciones se ejecutan en el orden correcto. El código debe tener este aspecto:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
  
#### <a name="to-test-the-application"></a>Para probar la aplicación  
  
1. Seleccione **F5**.  
  
2. Realice algunos cambios en los datos de uno o más registros de cada tabla.  
  
3. Seleccione el botón **Guardar**.  
  
4. Compruebe los valores de la base de datos para verificar que se guardaron los cambios.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se desea realizar después de crear un formulario enlazado a datos en la aplicación de Windows. Entre las mejoras que podría realizar se incluyen:  
  
- Agregar funcionalidad de búsqueda al formulario. Para obtener más información, vea [Cómo: Agregar una consulta parametrizada a un Windows Forms Application](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
- Editar el origen de datos para agregar o quitar objetos de base de datos. Para obtener más información, vea [Cómo: Editar un conjunto de datos](http://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
