---
title: Crear una aplicación de datos sencilla mediante ADO.NET en Visual Studio
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0c4e985231f8e74095add3e8a3a3e412814bed0d
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745807"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Crear una aplicación de datos sencilla mediante ADO.NET

Cuando se crea una aplicación que manipula datos en una base de datos, se realizan tareas básicas como definir cadenas de conexión, insertar datos y ejecutar procedimientos almacenados. Siguiendo este tema, puede detectar cómo interactuar con una base de datos dentro de una aplicación de "formularios sobre datos" de Windows Forms sencilla utilizando Visual C# o Visual Basic y ADO.NET.  Todas las tecnologías de datos. NET, incluidos los conjuntos de datos, LINQ to SQL y Entity Framework, en última instancia siga los pasos que son muy similares a las que se muestran en este artículo.

 Este artículo muestra una manera sencilla de obtener datos de una base de datos de una manera muy rápida. Si la aplicación necesita modificar los datos de maneras no trivial y actualizar la base de datos, debe considerar mediante Entity Framework y utilizar el enlace de datos para sincronizar automáticamente los controles de interfaz de usuario a los cambios en los datos subyacentes.

> [!IMPORTANT]
> Para simplificar el código, no se incluye el control de excepciones para entornos de producción.

## <a name="prerequisites"></a>Requisitos previos

Para crear la aplicación, necesitará:

-   Visual Studio.

-   SQL Server Express LocalDB. Si no tiene SQL Server Express LocalDB, puede instalarlo desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

En este tema se da por supuesto que está familiarizado con la funcionalidad básica del IDE de Visual Studio y puede crear una aplicación de formularios Windows Forms, agregar formularios al proyecto, colocar botones y otros controles en los formularios, establecer las propiedades de los controles y codificar eventos simples. Si no está familiarizado con estas tareas, recomendamos que complete la [Introducción a Visual C# y Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) tema antes de empezar este tutorial.

## <a name="set-up-the-sample-database"></a>Configurar la base de datos de ejemplo

Crear la base de datos de ejemplo, siga estos pasos:

1. En Visual Studio, abra el **Explorador de servidores** ventana.

2. Haga doble clic en **las conexiones de datos** y elija ** Crear nuevo servidor de base de datos SQL... ".

3. En el **nombre del servidor** texto cuadro, escriba **(localdb) \mssqllocaldb**.

4. En el **nuevo nombre de base de datos** texto cuadro, escriba **ventas**, a continuación, elija **Aceptar**.

     Vacío **ventas** base de datos se crea y se agrega al nodo Conexiones de datos en el Explorador de servidores.

5. Haga doble clic en el **ventas** conexión de datos y seleccione **nueva consulta**.

     Se abre una ventana del editor de consultas.

6. Copia la [script Transact-SQL de ventas](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) al Portapapeles.

7. Pegue el script de T-SQL en el editor de consultas y, a continuación, elija la **Execute** botón.

     Después de unos minutos, finaliza la ejecución de la consulta y se crean los objetos de base de datos. La base de datos contiene dos tablas: clientes y pedidos. Estas tablas no contienen datos inicialmente, pero puede agregar datos al ejecutar la aplicación que va a crear. La base de datos también contiene cuatro procedimientos almacenados simples.

## <a name="create-the-forms-and-add-controls"></a>Crear los formularios y agregar controles

1.  Cree un proyecto para una aplicación de formularios Windows Forms y, a continuación, asígnele el nombre SimpleDataApp.

     Visual Studio crea el proyecto y varios archivos, incluido un formulario de Windows Forms vacío denominado Form1.

2.  Agregue dos formularios Windows forms al proyecto para que tenga tres formularios y, a continuación, asígneles los nombres siguientes:

    -   Navegación

    -   NewCustomer

    -   FillOrCancel

3.  Para cada formulario, agregue los cuadros de texto, botones y otros controles que aparecen en las siguientes ilustraciones. Para cada control, establezca las propiedades que se describen en las tablas.

    > [!NOTE]
    >  El cuadro de grupo y los controles de etiquetas agregan claridad pero no se utilizan en el código.

 **Formulario Navigation**

 ![Cuadro de diálogo de navegación](../data-tools/media/simpleappnav.png)

|Controles del formulario Navigation|Propiedades|
|--------------------------------------|----------------|
|Botón|Nombre = btnGoToAdd|
|Botón|Nombre = btnGoToFillOrCancel|
|Botón|Nombre = btnExit|

 **Formulario NewCustomer**

 ![Agregar un nuevo cliente y realizar un pedido](../data-tools/media/simpleappnewcust.png)

|Controles del formulario NewCustomer|Propiedades|
|---------------------------------------|----------------|
|TextBox|Nombre = txtCustomerName|
|TextBox|Nombre = txtCustomerID<br /><br /> De solo lectura = True|
|Botón|Nombre = btnCreateAccount|
|NumericUpDown|Posiciones decimales = 0<br /><br /> Máximo = 5000<br /><br /> Nombre = numOrderAmount|
|DateTimePicker|Formato = Abreviado<br /><br /> Nombre = dtpOrderDate|
|Botón|Nombre = btnPlaceOrder|
|Botón|Nombre = btnAddAnotherAccount|
|Botón|Nombre = btnAddFinish|

 **Formulario FillOrCancel**

 ![rellenar o cancelar pedidos](../data-tools/media/simpleappcancelfill.png)

|Controles del formulario FillOrCancel|Propiedades|
|----------------------------------------|----------------|
|TextBox|Nombre = txtOrderID|
|Botón|Nombre = btnFindByOrderID|
|DateTimePicker|Formato = Abreviado<br /><br /> Nombre = dtpFillDate|
|DataGridView|Nombre = dgvCustomerOrders<br /><br /> De solo lectura = True<br /><br /> Encabezados de filas visibles = False|
|Botón|Nombre = btnCancelOrder|
|Botón|Nombre = btnFillOrder|
|Botón|Nombre = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Almacenar la cadena de conexión
 Cuando la aplicación intenta abrir una conexión a la base de datos, la aplicación debe tener acceso a la cadena de conexión. Para evitar introducir la cadena manualmente en cada formulario, almacenar la cadena en el archivo App.config en el proyecto y cree un método que devuelve la cadena cuando se llama al método desde cualquier formulario de la aplicación.

 Puede encontrar la cadena de conexión con el botón secundario en el **ventas** conexión de datos en **Explorador de servidores** y elegir **propiedades**. Busque la **ConnectionString** propiedad y, a continuación, use Ctrl + A Ctrl + C para seleccionar y copiar la cadena en el Portapapeles.

1.  Si está utilizando C#, en **el Explorador de soluciones**, expanda la **propiedades** nodo bajo el proyecto y, a continuación, abra el **Settings.settings** archivo.
    Si usa Visual Basic, en **el Explorador de soluciones**, haga clic en **mostrar todos los archivos**, expanda la **mi proyecto** nodo y, a continuación, abra el **Settings.settings** archivo.

2.  En el **nombre** columna, escriba `connString`.

3.  En el **tipo** lista, seleccione **(cadena de conexión)**.

4.  En el **ámbito** lista, seleccione **aplicación**.

5.  En el **valor** columna, escriba la cadena de conexión (sin ninguna fuera de las comillas) y, a continuación, guarde los cambios.

> [!NOTE]
> En una aplicación real, se debe almacenar la cadena de conexión de forma segura, como se describe en [las cadenas de conexión y archivos de configuración](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Escribir el código para los formularios

Esta sección contiene información general breve de lo que hace cada formulario. También proporciona el código que define la lógica subyacente cuando se hace clic en un botón del formulario.

### <a name="navigation-form"></a>Formulario Navigation

El formulario Navigation se abre cuando se ejecuta la aplicación. El **agregar una cuenta** botón abre el formulario NewCustomer. El **rellenar o cancelar pedidos** botón abre el formulario FillOrCancel. El **Exit** botón cierra la aplicación.

#### <a name="make-the-navigation-form-the-startup-form"></a>Hacer que el formulario Navigation sea el formulario de inicio

Si está utilizando C#, en **el Explorador de soluciones**, abra Program.cs y, a continuación, cambie la `Application.Run` línea a la siguiente: `Application.Run(new Navigation());`

Si usa Visual Basic, en **el Explorador de soluciones**, abra el **propiedades** ventana, seleccione la **aplicación** pestaña y, a continuación, seleccione  **SimpleDataApp.Navigation** en el **formulario de inicio** lista.

#### <a name="create-auto-generated-event-handlers"></a>Crear controladores de eventos generados automáticamente

Haga doble clic en los tres botones en el formulario de navegación para crear métodos de controlador de eventos vacío. Haga doble clic en los botones, también se agrega el código generado automáticamente en el archivo de código del diseñador que permite a un clic del botón Generar un evento.

#### <a name="add-code-for-the-navigation-form-logic"></a>Agregue código para la lógica del formulario de navegación

En la página de códigos del formulario Navigation, completa los cuerpos de método para el botón de tres controladores de eventos click tal como se muestra en el código siguiente.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formulario NewCustomer

Cuando escriba un nombre de cliente y, a continuación, seleccione la **crear cuenta** botón, el formulario NewCustomer crea una cuenta de cliente y SQL Server devuelve un valor de identidad como el nuevo identificador de cliente. A continuación, puede hacer un pedido para la nueva cuenta especificando una cantidad y una fecha de pedido y seleccionando la **realizar pedido** botón.

#### <a name="create-auto-generated-event-handlers"></a>Crear controladores de eventos generados automáticamente

Crear un Click vacío controlador de eventos para cada botón del formulario NewCustomer haciendo doble clic en cada uno de los cuatro botones. Haga doble clic en los botones, también se agrega el código generado automáticamente en el archivo de código del diseñador que permite a un clic del botón Generar un evento.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Agregue código para la lógica del formulario NewCustomer

Para completar la lógica del formulario NewCustomer, siga estos pasos.

1. Poner el `System.Data.SqlClient` en el ámbito de espacio de nombres para que le permitirá despreocuparse totalmente calificar los nombres de sus miembros.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Agregue algunas variables y métodos auxiliares a la clase como se muestra en el código siguiente.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Complete los cuerpos de método para el botón cuatro controladores de eventos click tal como se muestra en el código siguiente.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formulario FillOrCancel

El formulario FillOrCancel ejecuta una consulta que devuelve un pedido cuando escriba un identificador de pedido y, a continuación, haga clic en el **buscar pedido** botón. La fila devuelta aparece en una cuadrícula de datos de solo lectura. Puede marcar el pedido como cancelado (X) si selecciona el **Cancelar pedido** botón, o bien puede marcar el pedido como relleno (F) si selecciona el **rellenar pedido** botón. Si selecciona el **buscar pedido** nuevamente en el botón, la fila actualizada aparece.

#### <a name="create-auto-generated-event-handlers"></a>Crear controladores de eventos generados automáticamente

Crear vacío haga clic en controladores de eventos para los cuatro botones en el formulario FillOrCancel haciendo doble clic en los botones. Haga doble clic en los botones, también se agrega el código generado automáticamente en el archivo de código del diseñador que permite a un clic del botón Generar un evento.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Agregue código para la lógica del formulario FillOrCancel

Para completar la lógica del formulario FillOrCancel, siga estos pasos.

1. Devolver los siguientes dos espacios de nombres en el ámbito para que no tiene que calificar totalmente los nombres de sus miembros.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Agregue un variable y el método auxiliar a la clase como se muestra en el código siguiente.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Complete los cuerpos de método para el botón cuatro controladores de eventos click tal como se muestra en el código siguiente.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Probar la aplicación

Seleccione el **F5** clave para compilar y probar la aplicación después del código de cada controlador de eventos Click y, a continuación, después de finalizar la codificación.

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
