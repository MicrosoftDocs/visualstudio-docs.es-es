---
title: Guardar datos con los métodos DBDirect de TableAdapter | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655422"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Guardar datos con los métodos DBDirect de un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se proporcionan instrucciones detalladas para ejecutar instrucciones SQL directamente en una base de datos mediante los métodos DBDirect de un TableAdapter. Los métodos DBDirect de un TableAdapter proporcionan un nivel exhaustivo de control sobre las actualizaciones de la base de datos. Puede utilizarlos para ejecutar instrucciones SQL y procedimientos almacenados específicos mediante una llamada a los métodos individuales `Insert`, `Update` y `Delete` según sea necesario para la aplicación (en contraposición al método sobrecargado `Update` que realiza la actualización, INSERT y ELIMINAn todas las instrucciones en una llamada).

 Durante este tutorial aprenderá a:

- Cree una nueva **aplicación de Windows**.

- Crear y configurar un conjunto de datos con el [Asistente para la configuración de orígenes de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Cree un formulario enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.

- Agregue métodos para tener acceso directamente a la base de datos y realizar inserciones, actualizaciones y eliminaciones.

## <a name="prerequisites"></a>Requisitos previos
 Para poder completar este tutorial, necesitará:

- Acceso a la base de datos de ejemplo Northwind.

## <a name="create-a-windows-application"></a>Crear una aplicación para Windows
 El primer paso es crear una **aplicación para Windows**.

#### <a name="to-create-the-new-windows-project"></a>Para crear el nuevo proyecto de Windows

1. En Visual Studio, en el menú **archivo** , cree un nuevo **proyecto**.

2. Asigne al proyecto el nombre **TableAdapterDbDirectMethodsWalkthrough**.

3. Seleccione **aplicación para Windows**y, después, haga clic en **Aceptar**. Para obtener más información, vea [aplicaciones cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Se crea el proyecto **TableAdapterDbDirectMethodsWalkthrough** y se agrega al **Explorador de soluciones**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos a partir de la base de datos
 En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Region` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.

#### <a name="to-create-the-data-source"></a>Para crear el origen de datos

1. En el menú **datos** , seleccione **Mostrar orígenes de datos**.

2. En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. En la pantalla **elegir un tipo de origen de datos** , seleccione **base**de datos y, a continuación, seleccione **siguiente**.

4. En la pantalla **elegir la conexión de datos** , realice una de las acciones siguientes:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

         o bien

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si la base de datos requiere una contraseña, seleccione la opción para incluir la información confidencial y, a continuación, seleccione **siguiente**.

6. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , seleccione **siguiente**.

7. En la pantalla **elegir los objetos de base de datos** , expanda el nodo **tablas** .

8. Seleccione la tabla `Region` y, a continuación, seleccione **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y la tabla `Region` aparece en la ventana **Orígenes de datos**.

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols al formulario para mostrar los datos
 Cree los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para crear controles enlazados a datos en Windows Forms

- Arrastre el nodo de la **región** principal desde la ventana **orígenes de datos** hasta el formulario.

     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

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

- Seleccione el botón **Insertar** y compruebe que el nuevo registro aparece en la cuadrícula.

- Seleccione el botón **Actualizar** y compruebe que el registro se actualiza en la cuadrícula.

- Seleccione el botón **eliminar** y compruebe que el registro se ha quitado de la cuadrícula.

## <a name="next-steps"></a>Pasos siguientes
 En función de los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un formulario enlazado a datos. Entre las mejoras que podría realizar se incluyen:

- Agregar funcionalidad de búsqueda al formulario. Para obtener más información, consulte [Cómo: agregar una consulta parametrizada a una aplicación Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Agregar otras tablas al conjunto de datos seleccionando **Configurar DataSet con el asistente** en la ventana **Orígenes de datos**. Puede agregar controles que muestren los datos relacionados arrastrando los nodos relacionados al formulario.

## <a name="see-also"></a>Vea también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
