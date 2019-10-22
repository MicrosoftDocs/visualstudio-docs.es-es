---
title: Controlar una excepción de simultaneidad | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670036"
---
# <a name="handle-a-concurrency-exception"></a>Tratar las excepciones de simultaneidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las excepciones de simultaneidad (<xref:System.Data.DBConcurrencyException>) se producen cuando dos usuarios intentan cambiar los mismos datos al mismo tiempo en una base de datos. En este tutorial, creará una aplicación de Windows que muestra cómo detectar un <xref:System.Data.DBConcurrencyException>, buscar la fila que produjo el error y aprender una estrategia para controlarlo.

 Este tutorial le guía a través del proceso siguiente:

1. Cree un nuevo proyecto de **aplicación para Windows** .

2. Crear un nuevo conjunto de datos basado en la tabla `Customers` de Northwind.

3. Crear un formulario con un control <xref:System.Windows.Forms.DataGridView> para mostrar los datos.

4. Llenar un conjunto de datos con datos de la tabla `Customers` de la base de datos Northwind.

5. Utilice [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) en Visual Studio para tener acceso directamente a la tabla de datos de `Customers` y cambiar un registro.

6. Cambie el mismo registro a un valor diferente, actualice el conjunto de datos e intente escribir los cambios en la base de datos, lo que provocará que se produzca un error de simultaneidad.

7. Detectar el error y luego mostrar las diferentes versiones del registro, de modo que el usuario pueda determinar si continuar y actualizar la base de datos o cancelar la actualización.

## <a name="prerequisites"></a>Requisitos previos
 Para completar las tareas de este tutorial, necesitará:

- Acceso a la base de datos de ejemplo Northwind con permiso para realizar actualizaciones.

> [!NOTE]
> Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la ayuda, en función de la configuración activa o la edición que esté usando. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Crear un proyecto nuevo
 El primer paso del tutorial es crear una nueva aplicación para Windows.

#### <a name="to-create-a-new-windows-application-project"></a>Para crear un nuevo proyecto de aplicación para Windows

1. En el menú **archivo** , cree un nuevo proyecto.

2. En el panel **tipos de proyecto** , seleccione un lenguaje de programación.

3. En el panel **plantillas** , seleccione **aplicación para Windows**.

4. Asigne el nombre `ConcurrencyWalkthrough` al proyecto y seleccione **Aceptar**.

     Visual Studio agrega el proyecto a **Explorador de soluciones** y muestra un nuevo formulario en el diseñador.

## <a name="create-the-northwind-dataset"></a>Crear el conjunto de DataSet Northwind
 En esta sección, creará un conjunto de DataSet denominado `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>Para crear el conjunto de datos NorthwindDataSet

1. En el menú **datos** , elija **Agregar nuevo origen de datos**.

     Se abrirá el [Asistente para configuración de orígenes de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

2. En la pantalla **elegir un tipo de origen de datos**, seleccione **base**de datos.

3. Seleccione una conexión a la base de datos de ejemplo Northwind en la lista de conexiones disponibles. Si la conexión no está disponible en la lista de conexiones, seleccione**nueva conexión** .

    > [!NOTE]
    > Si se va a conectar a un archivo de base de datos local, seleccione **no** cuando se le pregunte si desea agregar el archivo al proyecto.

4. En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación**, seleccione **siguiente**.

5. Expanda el nodo **tablas** y seleccione la tabla `Customers`. El nombre predeterminado del conjunto de datos debería ser `NorthwindDataSet`.

6. Seleccione **Finalizar** para agregar el conjunto de DataSet al proyecto.

## <a name="create-a-data-bound-datagridview-control"></a>Crear un control DataGridView enlazado a datos
 En esta sección, creará una <xref:System.Windows.Forms.DataGridView> arrastrando el elemento **Customers** desde la ventana **orígenes de datos** hasta el Windows Form.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Para crear un control DataGridView enlazado a la tabla Customers

1. En el menú **datos** , elija **Mostrar orígenes de datos** para abrir la **ventana orígenes de datos**.

2. En la ventana **orígenes de datos** , expanda el nodo **NorthwindDataSet** y, a continuación, seleccione la tabla **Customers** .

3. Seleccione la flecha hacia abajo en el nodo de tabla y, a continuación, seleccione **DataGridView** en la lista desplegable.

4. Arrastre la tabla hasta un área vacía de su formulario.

     Un control <xref:System.Windows.Forms.DataGridView> denominado `CustomersDataGridView` y un <xref:System.Windows.Forms.BindingNavigator> denominado `CustomersBindingNavigator` se agregan al formulario que está enlazado al <xref:System.Windows.Forms.BindingSource>. esto, está en, se enlaza a la tabla `Customers` del `NorthwindDataSet`.

## <a name="test-the-form"></a>Prueba del formulario
 Ahora es posible comprobar el formulario para asegurarse de que se comporta de la forma prevista.

#### <a name="to-test-the-form"></a>Para comprobar el formulario

1. Seleccione **F5** para ejecutar la aplicación.

     El formulario aparece con un control <xref:System.Windows.Forms.DataGridView> en él que se rellena con los datos de la tabla `Customers`.

2. En el menú **depurar** , seleccione**detener depuración**.

## <a name="handleconcurrency-errors"></a>Errores de Handleconcurrency
 La forma de controlar los errores depende de las reglas de negocios específicas que rigen la aplicación. En este tutorial, usamos la estrategia siguiente como ejemplo de cómo tohandle el error de simultaneidad.

 Applicationpresents el usuario con tres versiones del registro:

- El registro actual en la base de datos.

- El registro original que se carga en el conjunto de registros

- Los cambios propuestos en el conjunto de datos

  Entonces, el usuario puede sobrescribir la base de datos con la versión propuesta o cancelar la actualización y actualizar el conjunto de datos con los nuevos valores de la base de datos.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Para habilitar el control de errores de simultaneidad

1. Crear un controlador de errores personalizado.

2. Presentar opciones al usuario.

3. Procesar la respuesta del usuario.

4. Reenviar la actualización o reestablecer los datos en el conjunto de datos.

### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode para controlar la excepción de simultaneidad
 Al intentar realizar una actualización y se genera una excepción, por lo general querrá hacer algo con la información proporcionada por la excepción generada.

 En esta sección, agregará código que intenta actualizar la base de datos. También puede controlar cualquier <xref:System.Data.DBConcurrencyException> que se pueda producir, así como cualquier otra excepción.

> [!NOTE]
> Los métodos `CreateMessage` y `ProcessDialogResults` se agregarán más adelante en este tutorial.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Para agregar control de errores para el error de simultaneidad

1. Agregue el código siguiente al método `Form1_Load`:

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Reemplace el método `CustomersBindingNavigatorSaveItem_Click` para llamar al método `UpdateDatabase` de manera que tenga el siguiente aspecto:

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices al usuario
 El código que acaba de escribir llama al procedimiento `CreateMessage` para mostrar información de error al usuario. En este tutorial, se usa un cuadro de mensaje para mostrar las distintas versiones del registro al usuario. Esto permite al usuario elegir si desea sobrescribir el registro con los cambios o cancelar la edición. Cuando el usuario selecciona una opción (hace clic en un botón) en el cuadro de mensaje, la respuesta se pasa al método `ProcessDialogResult`.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Para crear el mensaje que se mostrará al usuario

- Cree el mensaje agregando el código siguiente en el **Editor de código**. Escriba este código debajo del método `UpdateDatabase`.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Procesar la respuesta del usuario
 También necesita código para procesar la respuesta del usuario al cuadro de mensaje. Las opciones son para sobrescribir el registro actual en la base de datos con el cambio propuesto, o bien abandonar los cambios locales y actualizar la tabla de datos con el registro que se encuentra actualmente en la base de datos. Si el usuario elige sí, se llama al método <xref:System.Data.DataTable.Merge%2A> con el argumento *preserveChanges* establecido en `true`. Esto hace que el intento de actualización se realice correctamente, ya que la versión original del registro coincide ahora con el registro de la base de datos.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Para procesar la respuesta del usuario en el cuadro de mensaje

- Agregue el código siguiente debajo del código que se agregó en la sección anterior.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Prueba del formulario
 Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista. Para simular una infracción de la simultaneidad necesita cambiar los datos en la base de datos después de rellenar el NorthwindDataSet.

#### <a name="to-test-the-form"></a>Para comprobar el formulario

1. Seleccione **F5** para ejecutar la aplicación.

2. Después de que el formulario aparezca, ejecútelo y cambie al IDE de Visual Studio.

3. En el menú **Ver** , elija **Explorador de servidores**.

4. En el **Explorador de servidores**, expanda la conexión que utiliza la aplicación y, a continuación, expanda el nodo **Tablas**.

5. Haga clic con el botón secundario en la tabla **Customers** y seleccione **Mostrar datos de tabla**.

6. En el primer registro (`ALFKI`), cambie `ContactName` a `Maria Anders2`.

    > [!NOTE]
    > Navegue hasta una fila diferente para confirmar el cambio.

7. Cambie al formulario en ejecución de `ConcurrencyWalkthrough`.

8. En el primer registro del formulario (`ALFKI`), cambie `ContactName` a `Maria Anders1`.

9. Seleccione el botón **Guardar**.

     Se produce el error de simultaneidad y aparece el cuadro de mensaje.

10. Al seleccionar **no** se cancela la actualización y se actualiza el conjunto de datos con los valores que se encuentran actualmente en la base de datos. Si selecciona **sí** , se escribe el valor propuesto en la base de datos.

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)