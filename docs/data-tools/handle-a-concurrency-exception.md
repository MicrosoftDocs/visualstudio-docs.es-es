---
title: Controlar una excepción de simultaneidad
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 24338b2a6bc49a9a1a2a77e6395f60013c4465b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="handle-a-concurrency-exception"></a>Controlar una excepción de simultaneidad
Las excepciones de simultaneidad (<xref:System.Data.DBConcurrencyException>) se producen cuando dos usuarios intentan cambiar los mismos datos al mismo tiempo en una base de datos. En este tutorial, creará una aplicación de Windows que ilustra cómo detectar una <xref:System.Data.DBConcurrencyException>, busque la fila que produjo el error y obtenga información acerca de una estrategia para cómo controlarla.

 Este tutorial le guía a través del proceso siguiente:

1.  Cree un nuevo proyecto de  **aplicación de Windows Forms**.

2.  Crear un nuevo conjunto de datos basado en la tabla `Customers` de Northwind.

3.  Crear un formulario con un control <xref:System.Windows.Forms.DataGridView> para mostrar los datos.

4.  Llenar un conjunto de datos con datos de la tabla `Customers` de la base de datos Northwind.

5.  Use la **mostrar datos de tabla** característica de **Explorador de servidores** para tener acceso a la `Customers` datos y el cambio de un registro de la tabla.

6.  Cambiar el mismo registro a un valor diferente, actualizar el conjunto de datos e intentar escribir los cambios en la base de datos, lo que produce un error de simultaneidad.

7.  Detectar el error y luego mostrar las diferentes versiones del registro, de modo que el usuario pueda determinar si continuar y actualizar la base de datos o cancelar la actualización.

## <a name="prerequisites"></a>Requisitos previos
Este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. El instalador de Visual Studio, se puede instalar SQL Server Express LocalDB como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta...** .

       Se abre una ventana del editor de consultas.

    2. Copia la [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de T-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.

       Después de unos minutos, finaliza la ejecución de la consulta y se crea la base de datos Northwind.

> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de la configuración activa o la edición que esté usando. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 Iniciar el tutorial creando una nueva aplicación de Windows Forms.

#### <a name="to-create-a-new-windows-forms-application-project"></a>Para crear un nuevo proyecto de aplicación de Windows Forms

1. En Visual Studio, en el **archivo** menú, seleccione **New**, **proyecto...** .

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **escritorio clásico de Windows**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **ConcurrencyWalkthrough**y, a continuación, elija **Aceptar**.

     El **ConcurrencyWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**, y abre un nuevo formulario en el diseñador.

## <a name="create-the-northwind-dataset"></a>Crear el conjunto de datos Northwind
 En esta sección, creará un conjunto de datos denominado `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>Para crear el conjunto de datos NorthwindDataSet

1.  En el **datos** menú, elija **Agregar nuevo origen de datos**.

     El [Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) se abre.

2.  En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**.

3.  Seleccione una conexión a la base de datos de ejemplo Northwind desde la lista de conexiones disponibles. Si la conexión no está disponible en la lista de conexiones, seleccione **nueva conexión**

    > [!NOTE]
    >  Si se conecta a un archivo de base de datos local, seleccione **n** cuando se le pregunte si prefiere que desea agregar el archivo al proyecto.

4.  En el **Guardar cadena de conexión en el archivo de configuración de aplicación** pantalla, seleccione **siguiente**.

5.  Expanda el **tablas** nodo y seleccione el `Customers` tabla. El nombre predeterminado del conjunto de datos debería ser `NorthwindDataSet`.

6.  Seleccione **finalizar** para agregar el conjunto de datos al proyecto.

## <a name="create-a-data-bound-datagridview-control"></a>Crear un control DataGridView enlazado a datos
 En esta sección, creará un <xref:System.Windows.Forms.DataGridView> arrastrando el **clientes** de elementos de la **orígenes de datos** ventana hasta los formularios Windows Forms.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Para crear un control DataGridView enlazado a la tabla Customers

1.  En el **datos** menú, elija **Mostrar orígenes de datos** para abrir el **ventana Orígenes de datos**.

2.  En el **orígenes de datos** ventana, expanda la **NorthwindDataSet** nodo y, a continuación, seleccione la **clientes** tabla.

3.  Seleccione la flecha hacia abajo en el nodo de tabla y, a continuación, seleccione **DataGridView** en la lista desplegable.

4.  Arrastre la tabla hasta un área vacía de su formulario.

     A <xref:System.Windows.Forms.DataGridView> control denominado `CustomersDataGridView` y un <xref:System.Windows.Forms.BindingNavigator> denominado `CustomersBindingNavigator` se agregan al formulario que está enlazado a la <xref:System.Windows.Forms.BindingSource>. Esto es, a su vez depende de la `Customers` tabla el `NorthwindDataSet`.

## <a name="test-the-form"></a>Comprobar el formulario
 Ahora es posible comprobar el formulario para asegurarse de que se comporta de la forma prevista.

#### <a name="to-test-the-form"></a>Para comprobar el formulario

1.  Seleccione **F5** para ejecutar la aplicación

     El formulario aparece con un <xref:System.Windows.Forms.DataGridView> control en el mismo que se rellena con datos de la `Customers` tabla.

2.  En el **depurar** menú, seleccione **Detener depuración**.

## <a name="handle-concurrency-errors"></a>Controlar los errores de simultaneidad
 Cómo controlar errores depende de las reglas de negocios específicas que rigen la aplicación. En este tutorial, usamos la estrategia siguiente como ejemplo de cómo controlar el error de simultaneidad.

 La aplicación presenta al usuario tres versiones del registro:

-   El registro actual en la base de datos

-   El registro original que se carga en el conjunto de datos

-   Los cambios propuestos en el conjunto de datos

El usuario es capaz de sobrescribir la base de datos con la versión propuesta o cancelar la actualización y actualizar el conjunto de datos con los nuevos valores de la base de datos.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Para habilitar el control de errores de simultaneidad

1.  Crear un controlador de errores personalizado.

2.  Presentar opciones al usuario.

3.  Procesar la respuesta del usuario.

4.  Reenviar la actualización o reestablecer los datos en el conjunto de datos.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Agregue código para controlar la excepción de simultaneidad
 Cuando se intenta realizar una actualización pero se produce una excepción, por lo general desea hacer algo con la información proporcionada por la excepción.

 En esta sección, agregará código que intenta actualizar la base de datos. El usuario controle también cualquier <xref:System.Data.DBConcurrencyException> que se produzca, además de cualquier otra excepción.

> [!NOTE]
>  Los métodos `CreateMessage` y `ProcessDialogResults` se agregarán más adelante en este tutorial.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Para agregar control de errores para el error de simultaneidad

1.  Agregue el código siguiente al método `Form1_Load`:

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2.  Reemplace el método `CustomersBindingNavigatorSaveItem_Click` para llamar al método `UpdateDatabase` de manera que tenga el siguiente aspecto:

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Opciones de presentación para el usuario
 El código que acaba de escribir llama al procedimiento `CreateMessage` para mostrar información de error al usuario. En este tutorial, usa un cuadro de mensaje para mostrar las distintas versiones del registro para el usuario. Esto permite al usuario elegir si desea sobrescribir el registro con los cambios o cancelar la edición. Cuando el usuario selecciona una opción (hace clic en un botón) en el cuadro de mensaje, la respuesta se pasa al método `ProcessDialogResult`.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Para crear el mensaje que se mostrará al usuario

-   Cree el mensaje agregando el código siguiente a la **Editor de código**. Escriba este código debajo del método `UpdateDatabase`.

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Procesar la respuesta del usuario
 También se necesita código para procesar la respuesta del usuario en el cuadro de mensajes. Las opciones son sobrescribir el registro actual en la base de datos con el cambio propuesto o abandonar los cambios locales y actualizar la tabla de datos con el registro que está actualmente en la base de datos. Si el usuario elige Sí, el <xref:System.Data.DataTable.Merge%2A> método se llama con la *preserveChanges* establecido en `true`. Esto hace que el intento de actualización se realice correctamente, dado que la versión original del registro ahora coincide con el registro en la base de datos.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Para procesar la respuesta del usuario en el cuadro de mensaje

-   Agregue el código siguiente debajo del código que agregó en la sección anterior.

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Comprobar el formulario
 Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista. Para simular una infracción de la simultaneidad necesita cambiar los datos en la base de datos después de rellenar el NorthwindDataSet.

#### <a name="to-test-the-form"></a>Para comprobar el formulario

1.  Seleccione **F5** para ejecutar la aplicación.

2.  Después de que el formulario aparezca, ejecútelo y cambie al IDE de Visual Studio.

3.  En el **vista** menú, elija **Explorador de servidores**.

4.  En **Explorador de servidores**, expanda la conexión de la aplicación está utilizando y, a continuación, expanda el **tablas** nodo.

5.  Haga clic en el **clientes** de tabla y, a continuación, seleccione **mostrar datos de tabla**.

6.  En el primer registro (`ALFKI`) cambiar `ContactName` a `Maria Anders2`.

    > [!NOTE]
    >  Navegue hasta una fila diferente para confirmar el cambio.

7.  Cambie al formulario en ejecución de `ConcurrencyWalkthrough`.

8.  En el primer registro en el formulario (`ALFKI`), cambiar`ContactName` a `Maria Anders1`.

9. Seleccione el **guardar** botón.

     Se produce el error de simultaneidad y aparece el cuadro de mensaje.

10. Seleccionar **n** cancela la actualización y actualiza el conjunto de datos con los valores que se encuentran actualmente en la base de datos. Seleccionar **Sí** escribe el valor propuesto para la base de datos.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)