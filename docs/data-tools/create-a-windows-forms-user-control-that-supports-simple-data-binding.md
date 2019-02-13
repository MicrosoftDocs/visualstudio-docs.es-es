---
title: Crear un control de usuario que admita enlaces de datos simples
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 716366366bd9bb7514d042748b07dcb30a3567eb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923829"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos simple

Cuando muestra datos en formularios de las aplicaciones Windows, puede elegir controles existentes en el **Cuadro de herramientas** o crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Los controles que implementan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> pueden contener una propiedad que se puede enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.

Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Al crear controles para su uso en escenarios de enlace de datos, debe implementar uno de los atributos de enlace de datos siguientes:

|Uso de atributos de enlace de datos|
| - |
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. (Este proceso se describe en esta página del tutorial.)|
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

En este tutorial se crea un control simple que muestra los datos de una sola columna en una tabla. En este ejemplo se usa la columna `Phone` de la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario simple muestra los números de teléfono de clientes en un formato de número de teléfono estándar, utilizando un <xref:System.Windows.Forms.MaskedTextBox> y estableciendo la máscara en un número de teléfono.

Durante este tutorial aprenderá a:

-   Crear una nueva **aplicación de Windows Forms**.

-   Agregue un nuevo **Control de usuario** a su proyecto.

-   Diseñe visualmente el control de usuario.

-   Implemente el atributo `DefaultBindingProperty`.

-   Crear un conjunto de datos con el **configuración origen de datos** asistente.

-   Establezca la columna **Phone** de la ventana **Orígenes de datos** de forma que se use el nuevo control.

-   Cree un formulario para mostrar los datos en el nuevo control.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1.  Si no tiene SQL Server Express LocalDB, instálelo de desde el [página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o a través del **instalador de Visual Studio**. En el **instalador de Visual Studio**, puede instalar SQL Server Express LocalDB como parte de la **procesamiento y almacenamiento de datos** carga de trabajo, o como un componente individual.

2.  Instalar la base de datos de ejemplo Northwind, siga estos pasos:

    1. En Visual Studio, abra el **Explorador de objetos de SQL Server** ventana. (Explorador de objetos de SQL Server se instala como parte de la **procesamiento y almacenamiento de datos** carga de trabajo en el **instalador de Visual Studio**.) Expanda el **SQL Server** nodo. Haga doble clic en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copia el [script Transact-SQL de Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el Portapapeles. Este script de Transact-SQL crea la base de datos Northwind desde el principio y lo rellena con datos.

    3. Pegue el script de Transact-SQL en el editor de consultas y, a continuación, elija el **Execute** botón.

       Después de un breve tiempo, finalice la consulta y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de Windows Forms

El primer paso es crear un **aplicación de Windows Forms**:

1. En Visual Studio, en el **archivo** menú, seleccione **New** > **proyecto**.

2. Expanda el **Visual C#** o **Visual Basic** en el panel izquierdo, seleccione **Windows Desktop**.

3. En el panel central, seleccione la **aplicación de Windows Forms** tipo de proyecto.

4. Denomine el proyecto **Tutorialdecontrolsimple**y, a continuación, elija **Aceptar**.

     El proyecto **TutorialDeControlSimple** se crea y se agrega al **Explorador de soluciones**.

## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto

Este tutorial crea un control simple enlazable a datos desde un **Control de usuario**. Agregar un **Control de usuario** elemento a la **Tutorialdecontrolsimple** proyecto:

1.  En el menú **Proyecto**, elija **Agregar control de usuario**.

2.  Escriba **PhoneNumberBox** en el área Nombre y haga clic en **Agregar**.

     El control **PhoneNumberBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.

## <a name="design-the-phonenumberbox-control"></a>Diseñar el control PhoneNumberBox

En este tutorial se expande en las existentes <xref:System.Windows.Forms.MaskedTextBox> para crear el **PhoneNumberBox** control:

1.  Arrastre un control <xref:System.Windows.Forms.MaskedTextBox> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.

2.  Seleccione la etiqueta inteligente en el <xref:System.Windows.Forms.MaskedTextBox> que acaba de arrastrar y elija **Establecer máscara**.

3.  Seleccione **Número de teléfono** en el cuadro de diálogo **Máscara de entrada** y haga clic en **Aceptar** para establecer la máscara.

## <a name="add-the-required-data-binding-attribute"></a>Agregue el atributo de enlace de datos requerido

En el caso de los controles simples que admiten enlaces de datos, implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  Cambiar el **PhoneNumberBox** control a la vista código. (En el menú **Ver**, elija **Código**.)

2.  Reemplace el código en el **PhoneNumberBox** con lo siguiente:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  En el menú **Compilar** , elija **Compilar solución**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos de la base de datos

En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Customers` de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases de datos de ejemplo](../data-tools/installing-database-systems-tools-and-samples.md).

1.  Para abrir el **orígenes de datos** ventana, en el **datos** menú, haga clic en **Mostrar orígenes de datos**.

2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3.  En la página **Elegir un tipo de origen de datos**, seleccione **Base de datos** y después haga clic en **Siguiente**.

4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:

    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7.  Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8.  Seleccione la tabla `Customers` y después haga clic en **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y la tabla `Customers` aparece en la ventana **Orígenes de datos**.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Establecer la columna phone para utilizar el control PhoneNumberBox

Dentro de la ventana **Orígenes de datos** puede establecer el control que se va a crear antes de arrastrar elementos a un formulario:

1.  Abra **Form1** en el diseñador.

2.  Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

3.  Haga clic en la flecha de lista desplegable en el nodo **Customers** y elija **Detalles** de la lista de control.

4.  Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **Personalizar**.

5.  Seleccione **PhoneNumberBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.

6.  Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

Para crear controles enlazados a datos en el formulario, arrastre el método main **clientes** nodo desde el **orígenes de datos** ventana hasta el formulario y compruebe que la **PhoneNumberBox** control es utilizado para mostrar los datos en el **teléfono** columna.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Ejecutar la aplicación

Presione **F5** para ejecutar la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:

-   Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.

-   Crear controles que admitan escenarios de enlace a datos más complejos. Para obtener más información, consulte [crear un control de usuario de Windows Forms que admita el enlace de datos complejos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) y [crear un control de usuario de Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)