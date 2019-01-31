---
title: Tratar las excepciones de simultaneidad
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: df7d5295cdf9460c8f331b9bf2f49138f9a806ab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013657"
---
# <a name="handle-a-concurrency-exception"></a>Tratar las excepciones de simultaneidad

Las excepciones de simultaneidad (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) se producen cuando dos usuarios intentan cambiar los mismos datos al mismo tiempo en una base de datos. En este tutorial, creará una aplicación de Windows que ilustra cómo detectar una <xref:System.Data.DBConcurrencyException>, busque la fila que produjo el error y obtenga información sobre una estrategia para saber cómo controlarla.

Este tutorial le guía a través del proceso siguiente:

1. Cree un nuevo proyecto de  **aplicación de Windows Forms**.

2. Cree un nuevo conjunto de datos basado en la tabla Customers de Northwind.

3. Crear un formulario con un control <xref:System.Windows.Forms.DataGridView> para mostrar los datos.

4. Rellenar un conjunto de datos con datos de la tabla Customers de la base de datos Northwind.

5. Use la **mostrar datos de tabla** de características en **Explorador de servidores** para tener acceso a datos de la tabla Customers y cambiar un registro.

6. Cambiar el mismo registro en un valor diferente, actualizar el conjunto de datos e intenta escribir los cambios en la base de datos, lo que resulta en que se produzca un error de simultaneidad.

7. Detectar el error y luego mostrar las diferentes versiones del registro, de modo que el usuario pueda determinar si continuar y actualizar la base de datos o cancelar la actualización.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2. Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el instalador de Visual Studio.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-a-new-project"></a>Crear un proyecto nuevo

Empiece por crear una nueva aplicación de Windows Forms:

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **ConcurrencyWalkthrough**y, a continuación, elija **Aceptar**.

     El **ConcurrencyWalkthrough** se crea y se agrega al proyecto **el Explorador de soluciones**, y se abre un nuevo formulario en el diseñador.

## <a name="create-the-northwind-dataset"></a>Crear el conjunto de datos Northwind

A continuación, cree un conjunto de datos denominado **NorthwindDataSet**:

1. En el **datos** menú, elija **Agregar nuevo origen de datos**.

   Se abrirá el Asistente para configuración de orígenes de datos.

2. En el **elegir un tipo de origen de datos** pantalla, seleccione **base de datos**.

   ![Asistente para configuración de origen de datos en Visual Studio](media/data-source-configuration-wizard.png)

3. Seleccione una conexión a la base de datos de ejemplo Northwind desde la lista de conexiones disponibles. Si la conexión no está disponible en la lista de conexiones, seleccione **nueva conexión**.

    > [!NOTE]
    > Si se conecta a un archivo de base de datos local, seleccione **No** cuando se le pregunte si prefiere que desea agregar el archivo al proyecto.

4. En el **Guardar cadena de conexión en el archivo de configuración de aplicación** pantalla, seleccione **siguiente**.

5. Expanda el **tablas** nodo y seleccione el **clientes** tabla. El nombre predeterminado del conjunto de datos debe ser **NorthwindDataSet**.

6. Seleccione **finalizar** para agregar el conjunto de datos al proyecto.

## <a name="create-a-data-bound-datagridview-control"></a>Crear un control de DataGridView enlazado a datos

En esta sección, creará un <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> arrastrando el **clientes** de elemento de la **orígenes de datos** ventana hasta el formulario de Windows.

1. Para abrir el **orígenes de datos** ventana, en el **datos** menú, elija **Mostrar orígenes de datos**.

2. En el **orígenes de datos** ventana, expanda el **NorthwindDataSet** nodo y, a continuación, seleccione el **clientes** tabla.

3. Seleccione la flecha abajo en el nodo de tabla y, a continuación, seleccione **DataGridView** en la lista desplegable.

4. Arrastre la tabla hasta un área vacía de su formulario.

     Un <xref:System.Windows.Forms.DataGridView> control denominado **CustomersDataGridView**y un <xref:System.Windows.Forms.BindingNavigator> denominado **CustomersBindingNavigator**, se agregan al formulario que está enlazado a la <xref:System.Windows.Forms.BindingSource>. Esto, a su vez, depende de la tabla Customers en NorthwindDataSet.

## <a name="test-the-form"></a>Comprobar el formulario

Ahora es posible comprobar el formulario para asegurarse de que se comporta de la forma prevista.

1. Seleccione **F5** para ejecutar la aplicación.

     El formulario aparece con un <xref:System.Windows.Forms.DataGridView> control en él que se rellena con datos de la tabla Customers.

2. En el **depurar** menú, seleccione **Detener depuración**.

## <a name="handle-concurrency-errors"></a>Controlar los errores de simultaneidad

Cómo controlar los errores depende de las reglas de negocios específicas que rigen la aplicación. En este tutorial, usamos la estrategia siguiente como ejemplo de cómo controlar el error de simultaneidad.

La aplicación presentará al usuario tres versiones del registro:

- El registro actual en la base de datos.

- El registro original cargado en el conjunto de datos

- Los cambios propuestos en el conjunto de datos

Entonces, el usuario puede sobrescribir la base de datos con la versión propuesta o cancelar la actualización y actualizar el conjunto de datos con los nuevos valores de la base de datos.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Para habilitar el control de errores de simultaneidad

1. Crear un controlador de errores personalizado.

2. Presentar opciones al usuario.

3. Procesar la respuesta del usuario.

4. Reenviar la actualización o reestablecer los datos en el conjunto de datos.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Agregue código para controlar la excepción de simultaneidad

Cuando se intenta realizar una actualización y se produce una excepción, por lo general desea hacer algo con la información suministrada por la excepción producida. En esta sección, agregue código que intenta actualizar la base de datos. El usuario controle también cualquier <xref:System.Data.DBConcurrencyException> que puedan generarse, así como cualquier otra excepción.

> [!NOTE]
> El `CreateMessage` y `ProcessDialogResults` se agregan métodos más adelante en el tutorial.

1. Agregue el código siguiente al método `Form1_Load`:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. Reemplace el método `CustomersBindingNavigatorSaveItem_Click` para llamar al método `UpdateDatabase` de manera que tenga el siguiente aspecto:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>Presentar opciones al usuario

El código que acaba de escribir llama al procedimiento `CreateMessage` para mostrar información de error al usuario. En este tutorial, usará un cuadro de mensaje para mostrar las diferentes versiones del registro para el usuario. Esto permite al usuario elegir si desea sobrescribir el registro con los cambios o cancelar la edición. Cuando el usuario selecciona una opción (hace clic en un botón) en el cuadro de mensaje, la respuesta se pasa al método `ProcessDialogResult`.

Cree el mensaje agregando el código siguiente en el **Editor de código**. Escriba este código debajo del método `UpdateDatabase`:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>Procesar la respuesta del usuario

También necesita código para procesar la respuesta del usuario en el cuadro de mensaje. Las opciones son sobrescribir el registro actual en la base de datos con el cambio propuesto, o abandonar los cambios locales y actualizar la tabla de datos con el registro que está actualmente en la base de datos. Si el usuario elige **Sí**, <xref:System.Data.DataTable.Merge%2A> se llama al método con el *preserveChanges* establecido en **true**. Esto hace que el intento de actualización se realice correctamente, porque la versión original del registro ahora coincide con el registro en la base de datos.

Agregue el código siguiente debajo del código que agregó en la sección anterior:

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>Comprobar el formulario

Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista. Para simular una infracción de simultaneidad, cambia los datos en la base de datos después de rellenar el NorthwindDataSet.

1. Seleccione **F5** para ejecutar la aplicación.

2. Después de que el formulario aparezca, ejecútelo y cambie al IDE de Visual Studio.

3. En el **vista** menú, elija **Explorador de servidores**.

4. En el **Explorador de servidores**, expanda la conexión que utiliza la aplicación y, a continuación, expanda el nodo **Tablas**.

5. Haga clic en el **clientes** de tabla y, a continuación, seleccione **mostrar datos de tabla**.

6. En el primer registro (**ALFKI**), cambiar **ContactName** a **Maria Anders2**.

    > [!NOTE]
    > Navegue hasta una fila diferente para confirmar el cambio.

7. Cambie al formulario ConcurrencyWalkthrough en ejecución.

8. En el primer registro en el formulario (**ALFKI**), cambiar **ContactName** a **Maria Anders1**.

9. Seleccione el botón **Guardar**.

     Se produce el error de simultaneidad y aparece el cuadro de mensaje.

   Seleccionar **n** cancela la actualización y actualiza el conjunto de datos con los valores que están actualmente en la base de datos. Seleccionar **Sí** escribe el valor propuesto para la base de datos.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)