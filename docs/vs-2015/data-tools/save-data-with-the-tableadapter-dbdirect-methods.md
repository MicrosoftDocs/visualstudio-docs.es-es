---
title: Guardar datos con el DBDirect de TableAdapter métodos | Documentos de Microsoft
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cba6f91dd6dc0bb826531a312dc6ca5c94b21a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558758"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Guardar datos con los métodos DBDirect de un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial proporciona instrucciones detalladas para ejecutar instrucciones SQL directamente en una base de datos mediante los métodos DBDirect de un TableAdapter. Los métodos DBDirect de un TableAdapter proporcionan un nivel exhaustivo de control sobre las actualizaciones de la base de datos. Puede usar para ejecutar instrucciones SQL específicas y procedimientos almacenados mediante una llamada a la persona `Insert`, `Update`, y `Delete` métodos según sea necesario para la aplicación (en lugar de sobrecargado `Update` método que realiza la actualización Instrucciones INSERT y DELETE en una llamada).  
  
 Durante este tutorial aprenderá a:  
  
- Cree un nuevo **aplicación Windows**.  
  
- Crear y configurar un conjunto de datos con el [Asistente para configuración de origen de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
- Cree un formulario enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.  
  
- Agregar métodos para tener acceso a la base de datos y realizar inserciones, actualizaciones y eliminaciones directamente...  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
- Acceso a la base de datos de ejemplo Northwind.
  
## <a name="create-a-windows-application"></a>Crear una aplicación de Windows  
 El primer paso es crear un **aplicación Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows  
  
1. En Visual Studio, en el **archivo** menú, cree un nuevo **proyecto**.  
  
2. Denomine el proyecto **TableAdapterDbDirectMethodsWalkthrough**.  
  
3. Seleccione **aplicación Windows**y, a continuación, seleccione **Aceptar**. Para obtener más información, consulte [las aplicaciones cliente](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Se crea el proyecto **TableAdapterDbDirectMethodsWalkthrough** y se agrega al **Explorador de soluciones**.  
  
## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos  
 En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Region` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.
  
#### <a name="to-create-the-data-source"></a>Para crear el origen de datos  
  
1. En el **datos** menú, seleccione **Mostrar orígenes de datos**.  
  
2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3. En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**y, a continuación, seleccione **siguiente**.  
  
4. En el **elegir la conexión de datos** pantalla, realice una de las siguientes acciones:  
  
    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         -o bien-  
  
    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5. Si la base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y, a continuación, seleccione **siguiente**.  
  
6. En el **Guardar cadena de conexión en el archivo de configuración de la aplicación** pantalla, seleccione **siguiente**.  
  
7. En el **elija los objetos de base de datos** pantalla, expanda el **tablas** nodo.  
  
8. Seleccione el `Region` de tabla y, a continuación, seleccione **finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y la tabla `Region` aparece en la ventana **Orígenes de datos**.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols al formulario para mostrar los datos  
 Cree los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear datos enlazados a los controles del formulario de Windows  
  
- Arrastre el método main **región** nodo desde el **orígenes de datos** ventana hasta el formulario.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource>, y <xref:System.Windows.Forms.BindingNavigator> aparecen en la Bandeja de componentes.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Para agregar botones que llamarán a los métodos DbDirect de TableAdapter  
  
1. Arrastre tres controles <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** hasta **Form1** (debajo de **RegionDataGridView**).  
  
2. Establezca las propiedades **Nombre** y **Texto** en cada botón.  
  
    |Name|Text|  
    |----------|----------|  
    |`InsertButton`|**Insertar**|  
    |`UpdateButton`|**Actualizar**|  
    |`DeleteButton`|**Eliminar**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Para agregar código para insertar nuevos registros en la base de datos  
  
1. Seleccione **InsertButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.  
  
2. Reemplace el controlador de evento `InsertButton_Click` con el código siguiente:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Para agregar código para actualizar los registros de la base de datos  
  
1. Haga doble clic en **UpdateButton** para crear un controlador para el evento de clic y abrir el formulario en el editor de código.  
  
2. Reemplace el controlador de evento `UpdateButton_Click` con el código siguiente:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Para agregar código para eliminar registros de la base de datos  
  
1. Seleccione **DeleteButton** para crear un controlador de eventos para el evento de clic y abrir el formulario en el editor de código.  
  
2. Reemplace el controlador de evento `DeleteButton_Click` con el código siguiente:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Ejecutar la aplicación  
  
#### <a name="to-run-the-application"></a>Para ejecutar la aplicación  
  
- Seleccione **F5** para ejecutar la aplicación.  
  
- Seleccione el **insertar** botón y compruebe que el nuevo registro aparece en la cuadrícula.  
  
- Seleccione el **actualización** botón y compruebe que el registro se actualiza en la cuadrícula.  
  
- Seleccione el **eliminar** botón y compruebe que el registro se quita de la cuadrícula.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que se desea realizar después de crear un formulario enlazado a datos. Entre las mejoras que podría realizar se incluyen:  
  
- Agregar funcionalidad de búsqueda al formulario. Para obtener más información, vea [Cómo: Agregar una consulta parametrizada a un Windows Forms Application](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
- Agregar otras tablas al conjunto de datos seleccionando **Configurar DataSet con el asistente** en la ventana **Orígenes de datos**. Puede agregar controles que muestren los datos relacionados arrastrando los nodos relacionados al formulario. 
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
