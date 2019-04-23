---
title: Controlar una excepción de simultaneidad | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7ee82187adac74f90b6f5cb8485c68452d8329b0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060715"
---
# <a name="handle-a-concurrency-exception"></a>Tratar las excepciones de simultaneidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las excepciones de simultaneidad (<xref:System.Data.DBConcurrencyException>) se producen cuando dos usuarios intentan cambiar los mismos datos al mismo tiempo en una base de datos. En este tutorial, creará una aplicación de Windows que ilustra cómo detectar una <xref:System.Data.DBConcurrencyException>, busque la fila que produjo el error y obtenga información sobre una estrategia para saber cómo controlarla.  
  
 Este tutorial le guía a través del proceso siguiente:  
  
1. Cree un nuevo **aplicación Windows** proyecto.  
  
2. Crear un nuevo conjunto de datos basado en la tabla `Customers` de Northwind.  
  
3. Crear un formulario con un control <xref:System.Windows.Forms.DataGridView> para mostrar los datos.  
  
4. Llenar un conjunto de datos con datos de la tabla `Customers` de la base de datos Northwind.  
  
5. Use la [Visual Database Tools](http://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) en Visual Studio para tener acceso directamente a la `Customers` tabla de datos y cambiar un registro.  
  
6. Cambiar el mismo registro en un valor diferente, actualizar el conjunto de datos e intenta escribir los cambios en la base de datos, lo que resulta en que se produzca un error de simultaneidad.  
  
7. Detectar el error y luego mostrar las diferentes versiones del registro, de modo que el usuario pueda determinar si continuar y actualizar la base de datos o cancelar la actualización.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
- Acceso a la base de datos de ejemplo Northwind con permiso para realizar actualizaciones.
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la ayuda según la configuración activa o la edición que esté usando. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Crear un proyecto nuevo  
 El primer paso del tutorial es crear una nueva aplicación para Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Para crear un nuevo proyecto de aplicación de Windows  
  
1. En el **archivo** menú, cree un nuevo proyecto.  
  
2. En el **tipos de proyecto** panel, seleccione un lenguaje de programación.  
  
3. En el **plantillas** panel, seleccione **aplicación Windows**.  
  
4. Denomine el proyecto `ConcurrencyWalkthrough`y, a continuación, seleccione **Aceptar**.  
  
     Visual Studio agrega el proyecto al **el Explorador de soluciones** y muestra un formulario nuevo en el diseñador.  
  
## <a name="create-the-northwind-dataset"></a>Crear el conjunto de datos Northwind  
 En esta sección, creará un conjunto de datos denominado `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Para crear el conjunto de datos NorthwindDataSet  
  
1. En el **datos** menú, elija **Agregar nuevo origen de datos**.  
  
     Se abrirá el [Asistente para configuración de orígenes de datos](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
2. En el **elegir un tipo de origen de datos**pantalla, seleccione **base de datos**.  
  
3. Seleccione una conexión a la base de datos de ejemplo Northwind desde la lista de conexiones disponibles. Si la conexión no está disponible en la lista de conexiones, seleccione**nueva conexión**  
  
    > [!NOTE]
    >  Si se conecta a un archivo de base de datos local, seleccione **No** cuando se le pregunte si prefiere que desea agregar el archivo al proyecto.  
  
4. En el **Guardar cadena de conexión en el archivo de configuración de aplicación**pantalla, seleccione **siguiente**.  
  
5. Expanda el **tablas** nodo y seleccione el `Customers` tabla. El nombre predeterminado del conjunto de datos debería ser `NorthwindDataSet`.  
  
6. Seleccione **finalizar** para agregar el conjunto de datos al proyecto.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Crear un control de DataGridView enlazado a datos  
 En esta sección, creará un <xref:System.Windows.Forms.DataGridView> arrastrando el **clientes** de elemento de la **orígenes de datos** ventana hasta el formulario de Windows.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Para crear un control DataGridView enlazado a la tabla Customers  
  
1. En el **datos** menú, elija **Mostrar orígenes de datos** para abrir el **ventana Orígenes de datos**.  
  
2. En el **orígenes de datos** ventana, expanda el **NorthwindDataSet** nodo y, a continuación, seleccione el **clientes** tabla.  
  
3. Seleccione la flecha abajo en el nodo de tabla y, a continuación, seleccione **DataGridView** en la lista desplegable.  
  
4. Arrastre la tabla hasta un área vacía de su formulario.  
  
     Un <xref:System.Windows.Forms.DataGridView> control denominado `CustomersDataGridView` y un <xref:System.Windows.Forms.BindingNavigator> denominado `CustomersBindingNavigator` se agregan al formulario que está enlazado a la <xref:System.Windows.Forms.BindingSource>. Esto es, a su vez depende de la `Customers` de tabla en la `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Comprobar el formulario  
 Ahora es posible comprobar el formulario para asegurarse de que se comporta de la forma prevista.  
  
#### <a name="to-test-the-form"></a>Para comprobar el formulario  
  
1. Seleccione **F5** para ejecutar la aplicación  
  
     El formulario aparece con un <xref:System.Windows.Forms.DataGridView> control en él que se rellena con datos de la `Customers` tabla.  
  
2. En el **depurar** menú, seleccione**Detener depuración**.  
  
## <a name="handleconcurrency-errors"></a>Errores de Handleconcurrency  
 Cómo controlar errores depende de las reglas de negocios específicas que rigen la aplicación. En este tutorial, usamos la estrategia siguiente como ejemplo de cómo demanejar una el error de simultaneidad.  
  
 El usuario con las tres versiones del registro applicationpresents:  
  
- El registro actual en la base de datos.  
  
- El registro original cargado en el conjunto de datos  
  
- Los cambios propuestos en el conjunto de datos  
  
  Entonces, el usuario puede sobrescribir la base de datos con la versión propuesta o cancelar la actualización y actualizar el conjunto de datos con los nuevos valores de la base de datos.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Para habilitar el control de errores de simultaneidad  
  
1. Crear un controlador de errores personalizado.  
  
2. Presentar opciones al usuario.  
  
3. Procesar la respuesta del usuario.  
  
4. Reenviar la actualización o reestablecer los datos en el conjunto de datos.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode para controlar la excepción de simultaneidad  
 Cuando se intenta realizar una actualización y se produce una excepción, por lo general desea hacer algo con la información suministrada por la excepción producida.  
  
 En esta sección, agregue código que intenta actualizar la base de datos. El usuario controle también cualquier <xref:System.Data.DBConcurrencyException> que se produzca, así como cualquier otra excepción.  
  
> [!NOTE]
>  Los métodos `CreateMessage` y `ProcessDialogResults` se agregarán más adelante en este tutorial.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Para agregar control de errores para el error de simultaneidad  
  
1. Agregue el código siguiente al método `Form1_Load`:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2. Reemplace el método `CustomersBindingNavigatorSaveItem_Click` para llamar al método `UpdateDatabase` de manera que tenga el siguiente aspecto:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices al usuario  
 El código que acaba de escribir llama al procedimiento `CreateMessage` para mostrar información de error al usuario. En este tutorial, usará un cuadro de mensaje para mostrar las diferentes versiones del registro para el usuario. Esto permite al usuario elegir si desea sobrescribir el registro con los cambios o cancelar la edición. Cuando el usuario selecciona una opción (hace clic en un botón) en el cuadro de mensaje, la respuesta se pasa al método `ProcessDialogResult`.  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Para crear el mensaje que se mostrará al usuario  
  
- Cree el mensaje agregando el código siguiente en el **Editor de código**. Escriba este código debajo del método `UpdateDatabase`.  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Procesar la respuesta del usuario  
 También necesita código para procesar la respuesta del usuario en el cuadro de mensaje. Las opciones son sobrescribir el registro actual en la base de datos con el cambio propuesto, o abandonar los cambios locales y actualizar la tabla de datos con el registro que está actualmente en la base de datos. Si el usuario elige Sí, el <xref:System.Data.DataTable.Merge%2A> se llama al método con el *preserveChanges* establecido en `true`. Esto hace que el intento de actualización se realice correctamente, porque la versión original del registro ahora coincide con el registro en la base de datos.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Para procesar la respuesta del usuario en el cuadro de mensaje  
  
- Agregue el código siguiente debajo del código que agregó en la sección anterior.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Comprobar el formulario  
 Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista. Para simular una infracción de la simultaneidad necesita cambiar los datos en la base de datos después de rellenar el NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>Para comprobar el formulario  
  
1. Seleccione **F5** para ejecutar la aplicación.  
  
2. Después de que el formulario aparezca, ejecútelo y cambie al IDE de Visual Studio.  
  
3. En el **vista** menú, elija **Explorador de servidores**.  
  
4. En el **Explorador de servidores**, expanda la conexión que utiliza la aplicación y, a continuación, expanda el nodo **Tablas**.  
  
5. Haga clic en el **clientes** de tabla y, a continuación, seleccione **mostrar datos de tabla**.  
  
6. En el primer registro (`ALFKI`) cambiar `ContactName` a `Maria Anders2`.  
  
    > [!NOTE]
    >  Navegue hasta una fila diferente para confirmar el cambio.  
  
7. Cambie al formulario en ejecución de `ConcurrencyWalkthrough`.  
  
8. En el primer registro en el formulario (`ALFKI`), cambiar`ContactName` a `Maria Anders1`.  
  
9. Seleccione el botón **Guardar**.  
  
     Se produce el error de simultaneidad y aparece el cuadro de mensaje.  
  
10. Seleccionar **n** cancela la actualización y actualiza el conjunto de datos con los valores que están actualmente en la base de datos. Seleccionar **Sí** escribe el valor propuesto para la base de datos.
  
## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)