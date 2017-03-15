---
title: "Tutorial: Controlar una excepci&#243;n de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "control de simultaneidad, excepciones"
  - "control de simultaneidad, tutoriales"
  - "simultaneidad de datos, tutoriales"
  - "conjuntos de datos [Visual Basic], errores"
  - "control de excepciones, problemas de simultaneidad"
  - "actualizar conjuntos de datos, errores"
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 23
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Controlar una excepci&#243;n de simultaneidad
Las excepciones de simultaneidad \(<xref:System.Data.DBConcurrencyException>\) se producen cuando dos usuarios intentan cambiar los mismos datos al mismo tiempo en una base de datos.  En este tutorial creará una aplicación para Windows que ilustra cómo detectar una excepción <xref:System.Data.DBConcurrencyException>, ubicar la fila que produjo el error y una estrategia para controlarlo.  
  
 Este tutorial le guía a través del proceso siguiente:  
  
1.  Crear un proyecto nuevo de **aplicación para Windows**.  
  
2.  Crear un nuevo conjunto de datos basado en la tabla `Customers` de Northwind.  
  
3.  Crear un formulario con un control <xref:System.Windows.Forms.DataGridView> para mostrar los datos.  
  
4.  Llenar un conjunto de datos con datos de la tabla `Customers` de la base de datos Northwind.  
  
5.  Después de rellenar el conjunto de datos, utilizar [Visual Database Tools](http://msdn.microsoft.com/es-es/6b145922-2f00-47db-befc-bf351b4809a1) en Visual Studio para tener acceso directamente a la tabla de datos `Customers` y cambiar un registro.  
  
6.  A continuación, en el formulario, cambiar el mismo registro a un valor diferente, actualizar el conjunto de datos e intentar escribir los cambios en la base de datos, lo que hará que surja un error de simultaneidad.  
  
7.  Detectar el error y luego mostrar las diferentes versiones del registro, de modo que el usuario pueda determinar si continuar y actualizar la base de datos o cancelar la actualización.  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind con permiso para realizar actualizaciones.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Crear un proyecto nuevo  
 El primer paso del tutorial es crear una nueva aplicación para Windows.  
  
#### Para crear un proyecto de aplicación para Windows nuevo  
  
1.  Desde el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Seleccione un lenguaje de programación en el panel **Tipos de proyecto**.  
  
3.  Seleccione **Aplicación para Windows** en el panel **Plantillas**.  
  
4.  Denomine el proyecto `ConcurrencyWalkthrough`y, a continuación, haga clic en **Aceptar**.  
  
     Visual Studio agrega el proyecto al **Explorador de soluciones** y muestra un nuevo formulario en el diseñador.  
  
## Crear el conjunto de datos Northwind  
 En esta sección se creará un conjunto de datos denominado `NorthwindDataSet`.  
  
#### Para crear el conjunto de datos NorthwindDataSet  
  
1.  En el menú **Datos**, elija **Agregar nuevo origen de datos**.  
  
     Se abrirá el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
2.  Seleccione **Base de datos** en la página **Elegir un tipo de origen de datos**.  
  
3.  Seleccione una conexión a la base de datos de ejemplo Northwind desde la lista de conexiones disponibles o haga clic en **Nueva conexión** si la conexión no está disponible en la lista de conexiones.  
  
    > [!NOTE]
    >  Si intenta conectar a un archivo de la base de datos local, seleccione **No** cuando se le pregunte si desea agregar el archivo al proyecto.  
  
4.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
5.  Expanda el nodo **Tablas** y seleccione la tabla `Customers`.  El nombre predeterminado del conjunto de datos debería ser `NorthwindDataSet`.  
  
6.  Haga clic en **Finalizar** para agregar el conjunto de datos al proyecto.  
  
## Crear un control DataGridView enlazado a datos  
 En esta sección se creará un control <xref:System.Windows.Forms.DataGridView> arrastrando el elemento **Customers** desde la ventana **Orígenes de datos** hasta el Windows Form.  
  
#### Para crear un control DataGridView enlazado a la tabla Customers  
  
1.  En el menú **Datos**, elija **Mostrar orígenes de datos** para abrir la **Ventana de orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, expanda el nodo **NorthwindDataSet** y seleccione la tabla **Customers**.  
  
3.  Haga clic en la flecha hacia abajo del nodo de tabla y seleccione **DataGridView** en la lista desplegable.  
  
4.  Arrastre la tabla hasta un área vacía de su formulario.  
  
     Se agregan un control <xref:System.Windows.Forms.DataGridView> llamado `CustomersDataGridView` y un control <xref:System.Windows.Forms.BindingNavigator> denominado `CustomersBindingNavigator` al formulario enlazado con el <xref:System.Windows.Forms.BindingSource> que, a su vez, está enlazado con la tabla `Customers` del conjunto de datos `NorthwindDataSet`.  
  
## Punto de control  
 Ahora es posible comprobar el formulario para asegurarse de que se comporta de la forma prevista.  
  
#### Para comprobar el formulario  
  
1.  Presione F5 para ejecutar la aplicación.  
  
     El formulario aparece con un control <xref:System.Windows.Forms.DataGridView> que está relleno con los datos de la tabla `Customers`.  
  
2.  En el menú **Depurar**, elija **Detener depuración**.  
  
## Controlar errores de simultaneidad  
 La manera de controlar errores dependerá de los fines concretos para los que diseñe la aplicación.  Para este tutorial, después de que se produzca una infracción de simultaneidad, se utilizará la estrategia siguiente como ejemplo de control de errores de simultaneidad:  
  
 La aplicación presentará al usuario tres versiones del registro:  
  
-   El registro actual en la base de datos.  
  
-   El registro original cargado en el conjunto de datos.  
  
-   Los cambios propuestos en el conjunto de datos.  
  
 Entonces, el usuario puede sobrescribir la base de datos con la versión propuesta o cancelar la actualización y actualizar el conjunto de datos con los nuevos valores de la base de datos.  
  
#### Para habilitar el control de errores de simultaneidad  
  
1.  Crear un controlador de errores personalizado.  
  
2.  Presentar opciones al usuario.  
  
3.  Procesar la respuesta del usuario.  
  
4.  Reenviar la actualización o reestablecer los datos en el conjunto de datos.  
  
### Agregar Código para controlar la excepción de simultaneidad  
 Cuando intenta realizar una actualización pero se produce una excepción, puede utilizar la información que proporciona la excepción.  
  
 En esta sección agregará código que intentará actualizar la base de datos y controlará cualquier excepción <xref:System.Data.DBConcurrencyException> que se produzca, además de cualquier otra excepción.  
  
> [!NOTE]
>  Los métodos `CreateMessage` y `ProcessDialogResults` se agregarán más adelante en este tutorial.  
  
##### Para agregar control de errores para el error de simultaneidad  
  
1.  Agregue el código siguiente al método `Form1_Load`:  
  
     [!code-cs[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  Reemplace el método `CustomersBindingNavigatorSaveItem_Click` para llamar al método `UpdateDatabase` de manera que tenga el siguiente aspecto:  
  
     [!code-cs[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### Presentar opciones al usuario  
 El código que acaba de escribir llama al procedimiento `CreateMessage` para mostrar información de error al usuario.  En este tutorial, se usará un cuadro de mensaje para mostrar al usuario las distintas versiones del registro y permitirle elegir si desea sobrescribir el registro con los cambios o cancelar la edición.  Cuando el usuario selecciona una opción \(hace clic en un botón\) en el cuadro de mensaje, la respuesta se pasa al método `ProcessDialogResult`.  
  
##### Para crear el mensaje que se mostrará al usuario  
  
-   Cree el mensaje agregando el código siguiente en el **Editor de código**.  Escriba este código debajo del método `UpdateDatabase`.  
  
     [!code-cs[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### Procesar la respuesta del usuario  
 También necesitará código para procesar la respuesta del usuario al cuadro de mensaje.  Las opciones son sobrescribir el registro actual en la base de datos con el cambio propuesto o abandonar los cambios locales y actualizar la tabla de datos con el registro actual de la base de datos.  Si el usuario elige sí, se llama al método <xref:System.Data.DataTable.Merge%2A> con el argumento *preserveChanges* establecido en `true`.  Esto hará la actualización llegue a efectuarse, ya que ahora la versión original del registro coincide con el registro de la base de datos.  
  
##### Para procesar la respuesta del usuario en el cuadro de mensaje  
  
-   Agregue el código siguiente debajo del código agregado en la sección anterior.  
  
     [!code-cs[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## Pruebas  
 Puede comprobar el formulario para asegurarse de que se comporta de la forma prevista.  Para simular una infracción de la simultaneidad necesita cambiar los datos en la base de datos después de rellenar el NorthwindDataSet.  
  
#### Para comprobar el formulario  
  
1.  Presione F5 para ejecutar la aplicación.  
  
2.  Después de que el formulario aparezca, ejecútelo y cambie al IDE de Visual Studio.  
  
3.  En el menú **Ver**, elija **Explorador de servidores**.  
  
4.  En el **Explorador de servidores**, expanda la conexión que utiliza la aplicación y, a continuación, expanda el nodo **Tablas**.  
  
5.  Haga clic con el botón secundario del mouse en la tabla **Customers** y seleccione **Mostrar datos de tabla**.  
  
6.  En el primer registro \(`ALFKI`\), cambie el valor de `ContactName` a `Maria Anders2`.  
  
    > [!NOTE]
    >  Navegue hasta una fila diferente para confirmar el cambio.  
  
7.  Cambie al formulario en ejecución de `ConcurrencyWalkthrough`.  
  
8.  En el primer registro del formulario \(`ALFKI`\), cambie el valor de `ContactName` a `Maria Anders1`.  
  
9. Haga clic en el botón **Guardar**.  
  
     Se produce el error de simultaneidad y aparece el cuadro de mensaje.  
  
10. Al hacer clic en **No** se cancela la actualización y se actualiza el conjunto de datos con los valores existentes en ese momento en la base de datos, mientras que al hacer clic en **Sí**, se escribe en la base de datos el valor propuesto.  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)