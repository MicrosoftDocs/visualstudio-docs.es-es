---
title: Crear controles de usuario que admitan el enlace de datos simple
description: Aprenda a crear un control de usuario Windows Forms que admita el enlace de datos simple, mediante la clase DefaultBindingPropertyAttribute en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4ba2010b33b1defa6ef7dcb601fde9417fa47f70
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436750"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Crear un control de usuario de Windows Forms que admita el enlace de datos simple

Cuando muestra datos en formularios de las aplicaciones Windows, puede elegir controles existentes en el **Cuadro de herramientas** o crear controles personalizados si la aplicación requiere funcionalidad que no está disponible en los controles estándar. En este tutorial se muestra cómo crear un control que implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Los controles que implementan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> pueden contener una propiedad que se puede enlazar a datos. Tales controles son similares a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.

Para obtener más información sobre la creación de controles, vea [desarrollar controles de Windows Forms en tiempo de diseño](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Al crear controles para su uso en escenarios de enlace de datos, debe implementar uno de los siguientes atributos de enlace de datos:

|Uso de atributos de enlace de datos|
| - |
|Implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute> en controles sencillos, como un <xref:System.Windows.Forms.TextBox>, que muestra una única columna (o propiedad) de datos. (Este proceso se describe en esta página del tutorial.)|
|Implemente el <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.DataGridView>, que muestra listas (o tablas) de datos. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente el <xref:System.ComponentModel.LookupBindingPropertiesAttribute> en controles, como <xref:System.Windows.Forms.ComboBox>, que muestren listas (o tablas) de datos, pero que también necesiten presentar una única columna o propiedad. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

En este tutorial se crea un control simple que muestra los datos de una sola columna en una tabla. En este ejemplo se usa la columna `Phone` de la tabla `Customers` de la base de datos de ejemplo Northwind. El control de usuario simple muestra los números de teléfono de los clientes en un formato de número de teléfono estándar, mediante el uso de <xref:System.Windows.Forms.MaskedTextBox> y el establecimiento de la máscara en un número de teléfono.

Durante este tutorial aprenderá a:

- Cree una nueva **aplicación Windows Forms**.

- Agregue un nuevo **Control de usuario** a su proyecto.

- Diseñe visualmente el control de usuario.

- Implemente el atributo `DefaultBindingProperty`.

- Cree un conjunto de datos con el Asistente para la **configuración de orígenes de datos** .

- Establezca la columna **Phone** de la ventana **Orígenes de datos** de forma que se use el nuevo control.

- Cree un formulario para mostrar los datos en el nuevo control.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa SQL Server Express LocalDB y la base de datos de ejemplo Northwind.

1. Si no tiene SQL Server Express LocalDB, instálelo desde la [Página de descarga de SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o a través de la **instalador de Visual Studio**. En el **instalador de Visual Studio** , puede instalar SQL Server Express LocalDB como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** , o como un componente individual.

2. Instale la base de datos de ejemplo Northwind siguiendo estos pasos:

    1. En Visual Studio, abra la ventana **Explorador de objetos de SQL Server** . (Explorador de objetos de SQL Server se instala como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el **instalador de Visual Studio** ). Expanda el nodo **SQL Server** . Haga clic con el botón secundario en la instancia de LocalDB y seleccione **nueva consulta**.

       Se abre una ventana del editor de consultas.

    2. Copie el [script de Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) en el portapapeles. Este script T-SQL crea la base de datos Northwind desde cero y la rellena con datos.

    3. Pegue el script T-SQL en el editor de consultas y, a continuación, elija el botón **Ejecutar** .

       Tras un breve período de tiempo, la consulta termina de ejecutarse y se crea la base de datos Northwind.

## <a name="create-a-windows-forms-application"></a>Crear una aplicación de Windows Forms

El primer paso es crear una **aplicación Windows Forms** :

1. En Visual Studio, en el menú **Archivo** , seleccione **Nuevo** > **Proyecto**.

2. Expanda **Visual C#** o **Visual Basic** en el panel izquierdo y, a continuación, seleccione **escritorio de Windows**.

3. En el panel central, seleccione el tipo de proyecto **Windows Forms aplicación** .

4. Asigne al proyecto el nombre **tutorialdecontrolsimple** y, a continuación, elija **Aceptar**.

     El proyecto **TutorialDeControlSimple** se crea y se agrega al **Explorador de soluciones**.

## <a name="add-a-user-control-to-the-project"></a>Agregar un control de usuario al proyecto

En este tutorial se crea un control simple enlazable a datos a partir de un **control de usuario**. Agregue un elemento de **control de usuario** al proyecto **tutorialdecontrolsimple** :

1. En el menú **Proyecto** , elija **Agregar control de usuario**.

2. Escriba **PhoneNumberBox** en el área Nombre y haga clic en **Agregar**.

     El control **PhoneNumberBox** se agrega al **Explorador de soluciones** y se abre en el diseñador.

## <a name="design-the-phonenumberbox-control"></a>Diseñar el control PhoneNumberBox

En este tutorial se amplía el existente <xref:System.Windows.Forms.MaskedTextBox> para crear el control **PhoneNumberBox** :

1. Arrastre un control <xref:System.Windows.Forms.MaskedTextBox> del **Cuadro de herramientas** hasta la superficie de diseño del control del usuario.

2. Seleccione la etiqueta inteligente en el <xref:System.Windows.Forms.MaskedTextBox> que acaba de arrastrar y elija **Establecer máscara**.

3. Seleccione **Número de teléfono** en el cuadro de diálogo **Máscara de entrada** y haga clic en **Aceptar** para establecer la máscara.

## <a name="add-the-required-data-binding-attribute"></a>Agregar el atributo de enlace de datos requerido

En el caso de los controles simples que admiten enlaces de datos, implemente el <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1. Cambie el control **PhoneNumberBox** a la vista de código. (En el menú **Ver** , elija **Código**.)

2. Reemplace el código de **PhoneNumberBox** por lo siguiente:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. En el menú **Compilar** , elija **Compilar solución**.

## <a name="create-a-data-source-from-your-database"></a>Crear un origen de datos a partir de la base de datos

En este paso se usa el Asistente para la **configuración de orígenes de datos** para crear un origen de datos basado en la `Customers` tabla de la base de datos de ejemplo Northwind. Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión. Para obtener información acerca de cómo configurar la base de datos de ejemplo Northwind, vea [Cómo: instalar bases](../data-tools/installing-database-systems-tools-and-samples.md)de datos de ejemplo.

1. Para abrir la ventana **orígenes de datos** , en el menú **datos** , haga clic en **Mostrar orígenes de datos**.

2. En la ventana **orígenes de datos** , seleccione **Agregar nuevo origen de datos** para iniciar el Asistente para la configuración de orígenes de **datos** .

3. En la página **Elegir un tipo de origen de datos** , seleccione **Base de datos** y después haga clic en **Siguiente**.

4. En la página **elegir la conexión de datos** , realice una de las acciones siguientes:

    - Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.

    - Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.

5. Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.

6. Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.

7. Expanda el nodo **Tablas** en la página **Elija los objetos de base de datos**.

8. Seleccione la tabla `Customers` y después haga clic en **Finalizar**.

     **NorthwindDataSet** se agrega al proyecto y la `Customers` tabla aparece en la ventana orígenes de **datos** .

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Establecer la columna Phone para usar el control PhoneNumberBox

Dentro de la ventana **orígenes de datos** , puede establecer el control que se va a crear antes de arrastrar elementos al formulario:

1. Abra **Form1** en el diseñador.

2. Expanda el nodo **Customers** en la ventana **Orígenes de datos**.

3. Haga clic en la flecha de lista desplegable en el nodo **Customers** y elija **Detalles** de la lista de control.

4. Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **Personalizar**.

5. Seleccione **PhoneNumberBox** de la lista de **Controles asociados** en el cuadro de diálogo **Opciones de personalización de la interfaz de usuario de datos**.

6. Haga clic en la flecha de lista desplegable en la columna **Phone** y elija **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Agregar controles al formulario

Puede crear los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.

Para crear controles enlazados a datos en el formulario, arrastre el nodo principal **Customers** desde la ventana **orígenes de datos** hasta el formulario y compruebe que el control **PhoneNumberBox** se utiliza para mostrar los datos en la columna **Phone** .

Los controles enlazados a datos con etiquetas descriptivas aparecen en el formulario, junto con una barra de herramientas (<xref:System.Windows.Forms.BindingNavigator>) para navegar por los registros. En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.

## <a name="run-the-application"></a>Ejecución de la aplicación

Presione **F5** para ejecutar la aplicación.

## <a name="next-steps"></a>Pasos siguientes

Según cuáles sean los requisitos de la aplicación, hay varios pasos que se pueden realizar después de crear un control que admite el enlace a datos. Entre los pasos más habituales están los siguientes:

- Colocar los controles personalizados en una biblioteca de controles para poder reutilizarlos en otras aplicaciones.

- Crear controles que admitan escenarios de enlace a datos más complejos. Para obtener más información, vea [crear un control de usuario Windows Forms que admita el enlace de datos complejo](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) y [crear un control de usuario Windows Forms que admita el enlace de datos de búsqueda](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte también

- [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
