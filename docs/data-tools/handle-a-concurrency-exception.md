---
title: Tratar las excepciones de simultaneidad
description: Controlar una excepción de simultaneidad (System. Data. DBConcurrencyException), que se genera cuando dos usuarios intentan cambiar los mismos datos en una base de datos al mismo tiempo.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f84fbaae3273b8830cce1c39cc3e42b62e487d3e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216246"
---
# <a name="handle-a-concurrency-exception"></a>Tratar las excepciones de simultaneidad

Las excepciones de simultaneidad (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>) se producen cuando dos usuarios intentan cambiar los mismos datos al mismo tiempo en una base de datos. En este tutorial, creará una aplicación de Windows que muestra cómo detectar <xref:System.Data.DBConcurrencyException> , buscar la fila que produjo el error y aprender una estrategia para controlarla.

Este tutorial le guía a través del proceso siguiente:

1. Cree un nuevo proyecto de **aplicación de Windows Forms** .

2. Cree un nuevo conjunto de DataSet basado en la tabla Northwind customers.

3. Crear un formulario con un control <xref:System.Windows.Forms.DataGridView> para mostrar los datos.

4. Rellene un conjunto de datos con datos de la tabla Customers de la base de datos Northwind.

5. Use la característica **Mostrar datos de tabla** en **Explorador de servidores** para tener acceso a los datos de la tabla de clientes y cambiar un registro.

6. Cambie el mismo registro a un valor diferente, actualice el conjunto de datos e intente escribir los cambios en la base de datos, lo que provocará que se produzca un error de simultaneidad.

7. Detectar el error y luego mostrar las diferentes versiones del registro, de modo que el usuario pueda determinar si continuar y actualizar la base de datos o cancelar la actualización.

## <a name="prerequisites"></a>Prerrequisitos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-new-project"></a>Creación de un nuevo proyecto

Empiece por crear una nueva aplicación de Windows Forms:

1. En Visual Studio, en el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **ConcurrencyWalkthrough** y, a continuación, elija **Aceptar**.

     El proyecto **ConcurrencyWalkthrough** se crea y se agrega a **Explorador de soluciones** y se abre un nuevo formulario en el diseñador.

## <a name="create-the-northwind-dataset"></a>Crear el conjunto de DataSet Northwind

A continuación, cree un conjunto de DataSet denominado **NorthwindDataSet**:

1. En el menú **datos** , elija **Agregar nuevo origen de datos**.

   Se abrirá el Asistente para configuración de orígenes de datos.

2. En la pantalla **elegir un tipo de origen de datos** , seleccione **base** de datos.

   ![Asistente para la configuración de orígenes de datos en Visual Studio](media/data-source-configuration-wizard.png)

3. Seleccione una conexión a la base de datos de ejemplo Northwind en la lista de conexiones disponibles. Si la conexión no está disponible en la lista de conexiones, seleccione **nueva conexión**.

    > [!NOTE]
    > Si se va a conectar a un archivo de base de datos local, seleccione **no** cuando se le pregunte si desea agregar el archivo al proyecto.

4. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación** , seleccione **siguiente**.

5. Expanda el nodo **tablas** y seleccione la tabla **Customers** . El nombre predeterminado del conjunto de valores debe ser **NorthwindDataSet**.

6. Seleccione **Finalizar** para agregar el conjunto de DataSet al proyecto.

## <a name="create-a-data-bound-datagridview-control"></a>Crear un control DataGridView enlazado a datos

En esta sección, creará un <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> arrastrando el elemento **Customers** desde la ventana **orígenes de datos** hasta el Windows Form.

1. Para abrir la ventana **orígenes de datos** , en el menú **datos** , elija **Mostrar orígenes de datos**.

2. En la ventana **orígenes de datos** , expanda el nodo **NorthwindDataSet** y, a continuación, seleccione la tabla **Customers** .

3. Seleccione la flecha hacia abajo en el nodo de tabla y, a continuación, seleccione **DataGridView** en la lista desplegable.

4. Arrastre la tabla hasta un área vacía de su formulario.

     Un <xref:System.Windows.Forms.DataGridView> control denominado **CustomersDataGridView**, y un <xref:System.Windows.Forms.BindingNavigator> **CustomersBindingNavigator** con nombre, se agregan al formulario que está enlazado a <xref:System.Windows.Forms.BindingSource> . Esto, a su vez, está enlazado a la tabla Customers de NorthwindDataSet.

## <a name="test-the-form"></a>Prueba del formulario

Ahora es posible comprobar el formulario para asegurarse de que se comporta de la forma prevista.

1. Seleccione **F5** para ejecutar la aplicación.

     El formulario aparece con un <xref:System.Windows.Forms.DataGridView> control que se rellena con los datos de la tabla customers.

2. En el menú **Depurar**, seleccione **Detener depuración**.

## <a name="handle-concurrency-errors"></a>Control de errores de simultaneidad

La forma de controlar los errores depende de las reglas de negocios específicas que rigen la aplicación. En este tutorial, usamos la estrategia siguiente como ejemplo de cómo controlar el error de simultaneidad.

La aplicación presenta al usuario tres versiones del registro:

- El registro actual en la base de datos.

- El registro original que se carga en el conjunto de registros

- Los cambios propuestos en el conjunto de datos

Entonces, el usuario puede sobrescribir la base de datos con la versión propuesta o cancelar la actualización y actualizar el conjunto de datos con los nuevos valores de la base de datos.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Para habilitar el control de errores de simultaneidad

1. Crear un controlador de errores personalizado.

2. Presentar opciones al usuario.

3. Procesar la respuesta del usuario.

4. Reenviar la actualización o reestablecer los datos en el conjunto de datos.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Agregar código para controlar la excepción de simultaneidad

Cuando se intenta realizar una actualización y se genera una excepción, normalmente se desea hacer algo con la información proporcionada por la excepción generada. En esta sección, agregará código que intenta actualizar la base de datos. También puede controlar cualquier <xref:System.Data.DBConcurrencyException> que se produzca, así como cualquier otra excepción.

> [!NOTE]
> Los `CreateMessage` `ProcessDialogResults` métodos y se agregan más adelante en el tutorial.

1. Agregue el código siguiente al método `Form1_Load`:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet1":::

2. Reemplace el método `CustomersBindingNavigatorSaveItem_Click` para llamar al método `UpdateDatabase` de manera que tenga el siguiente aspecto:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet2":::

### <a name="display-choices-to-the-user"></a>Presentar opciones al usuario

El código que acaba de escribir llama al procedimiento `CreateMessage` para mostrar información de error al usuario. En este tutorial, se usa un cuadro de mensaje para mostrar las distintas versiones del registro al usuario. Esto permite al usuario elegir si desea sobrescribir el registro con los cambios o cancelar la edición. Cuando el usuario selecciona una opción (hace clic en un botón) en el cuadro de mensaje, la respuesta se pasa al método `ProcessDialogResult`.

Cree el mensaje agregando el código siguiente en el **Editor de código**. Escriba este código debajo del método `UpdateDatabase`:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet4":::

### <a name="process-the-users-response"></a>Procesar la respuesta del usuario

También necesita código para procesar la respuesta del usuario al cuadro de mensaje. Las opciones son para sobrescribir el registro actual en la base de datos con el cambio propuesto, o bien abandonar los cambios locales y actualizar la tabla de datos con el registro que se encuentra actualmente en la base de datos. Si el usuario elige **sí**, <xref:System.Data.DataTable.Merge%2A> se llama al método con el argumento *preserveChanges* establecido en **true**. Esto hace que el intento de actualización se realice correctamente, ya que la versión original del registro coincide ahora con el registro de la base de datos.

Agregue el código siguiente debajo del código que se agregó en la sección anterior:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form-behavior"></a>Probar el comportamiento del formulario

Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista. Para simular una infracción de simultaneidad, cambie los datos en la base de datos después de llenar el NorthwindDataSet.

1. Seleccione **F5** para ejecutar la aplicación.

2. Después de que el formulario aparezca, ejecútelo y cambie al IDE de Visual Studio.

3. En el menú **Ver**, elija **Explorador de servidores**.

4. En el **Explorador de servidores**, expanda la conexión que utiliza la aplicación y, a continuación, expanda el nodo **Tablas**.

5. Haga clic con el botón secundario en la tabla **Customers** y seleccione **Mostrar datos de tabla**.

6. En el primer registro (**ALFKI**), cambie **ContactName** a **Maria Anders2**.

    > [!NOTE]
    > Navegue hasta una fila diferente para confirmar el cambio.

7. Cambie al formulario de ejecución de ConcurrencyWalkthrough.

8. En el primer registro del formulario (**ALFKI**), cambie **ContactName** por **María Anders1**.

9. Seleccione el botón **Guardar**.

     Se produce el error de simultaneidad y aparece el cuadro de mensaje.

   Al seleccionar **no** se cancela la actualización y se actualiza el conjunto de datos con los valores que se encuentran actualmente en la base de datos. Si selecciona **sí** , se escribe el valor propuesto en la base de datos.

## <a name="see-also"></a>Consulte también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
