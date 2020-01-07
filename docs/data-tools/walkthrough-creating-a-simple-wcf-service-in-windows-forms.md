---
title: 'Tutorial: Creación de un servicio WCF sencillo en Windows Forms'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3d3f2e80ff3e2b94c46d1e2658c40bccf2e6c365
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586021"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Tutorial: crear un servicio WCF simple en Windows Forms

En este tutorial se muestra cómo crear un servicio de Windows Communication Foundation simple (WCF), probarlo y, a continuación, acceder a él desde una aplicación Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Creación de un servicio

1. Abra Visual Studio.

::: moniker range="vs-2017"

2. En el menú **archivo** , elija **nuevo** **proyecto**de >.

3. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual Basic** o **Visual C#**  y elija **WCF**, seguido de la **biblioteca de servicios de WCF**.

4. Haga clic en **Aceptar** para crear el proyecto.

   ![El proyecto de biblioteca de servicios de WCF](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. Escriba **biblioteca de servicios WCF** en el cuadro de búsqueda de la página **crear un nuevo proyecto** . Seleccione la plantilla C# o Visual Basic de la **biblioteca de servicios WCF**y, a continuación, haga clic en **siguiente**.

   ![Crear un nuevo proyecto de biblioteca de servicios WCF en Visual Studio 2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Si no ve ninguna plantilla, es posible que deba instalar el componente de **Windows Communication Foundation** de Visual Studio. Elija **instalar más herramientas y características** para abrir instalador de Visual Studio. Elija la pestaña **componentes individuales** , desplácese hacia abajo hasta **actividades de desarrollo**y, a continuación, seleccione **Windows Communication Foundation**. Haga clic en **Modificar**.

4. En la página **configurar el nuevo proyecto** , haga clic en **crear**.

::: moniker-end

   > [!NOTE]
   > Se creará un servicio de trabajo que puede probar y acceder a él. Los dos pasos siguientes muestran cómo puede modificar el método predeterminado para utilizar un tipo de datos diferente. En una aplicación real, también agregaría sus propias funciones al servicio.

5. En **Explorador de soluciones**, haga doble clic en **IService1. VB** o **IService1.CS**.

   ![El archivo IService1](../data-tools/media/wcf2.png)

   Busque la línea siguiente:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Cambie el tipo del parámetro `value` a cadena:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   En el código anterior, observe los atributos `<OperationContract()>` o `[OperationContract]`. Estos atributos son obligatorios para cualquier método expuesto por el servicio.

6. En **Explorador de soluciones**, haga doble clic en **Service1. VB** o **Service1.CS**.

   ![El archivo Service1](../data-tools/media/wcf3.png)

   Busque la línea siguiente:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Cambie el tipo del parámetro `value` a cadena:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Probar el servicio

1. Presione **F5** para ejecutar el servicio. Aparece un formulario de **cliente de prueba WCF** y carga el servicio.

2. En el formulario **Cliente de prueba WCF**, haga doble clic en el método **GetData()** en **IService1**. Aparece la pestaña **GetData** .

     ![El método&#40; &#41; GetData](../data-tools/media/wcf4.png)

3. En el cuadro **Solicitar**, seleccione el campo **Valor** y escriba `Hello`.

     ![El campo Valor](../data-tools/media/wcf5.png)

4. Haga clic en el botón **Invocar**. Si aparece un cuadro de diálogo de **Advertencia de seguridad** , haga clic en **Aceptar**. El resultado se muestra en el cuadro **respuesta** .

     ![El resultado en el cuadro Respuesta](../data-tools/media/wcf6.png)

5. En el menú **Archivo**, haga clic en **Salir** para cerrar el formulario de prueba.

## <a name="access-the-service"></a>Acceso al servicio

### <a name="reference-the-wcf-service"></a>Referencia al servicio WCF

1. En el menú **Archivo**, apunte a **Agregar**y haga clic en **Nuevo proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , expanda el nodo **Visual Basic** o **Visual C#**  , seleccione **Windows**y, a continuación, seleccione **aplicación de Windows Forms**. Haga clic en **Aceptar** para abrir el proyecto.

     ![Proyecto de Aplicación de Windows Forms](../data-tools/media/wcf7.png)

3. Haga clic con el botón derecho en **WindowsApplication1** y haga clic en **Agregar referencia de servicio**. Aparece el cuadro de diálogo **Agregar referencia de servicio** .

4. En el cuadro de diálogo **Agregar referencia de servicio**, haga clic en **Detectar**.

     ![El cuadro de diálogo Agregar referencia de servicio](../data-tools/media/wcf8.png)

     **Service1** se muestra en el panel **servicios** .

5. Haga clic en **Aceptar** para agregar la referencia del servicio.

### <a name="build-a-client-application"></a>Compilar una aplicación cliente

1. En el **Explorador de soluciones**, haga doble clic en **Form1.vb** o **Form1.cs** para abrir el Diseñador de Windows Forms, si no está ya abierto.

2. Desde el **Cuadro de herramientas**, arrastre un control `TextBox`, un control `Label` y un control `Button` al formulario.

     ![Agregar controles al formulario](../data-tools/media/wcf9.png)

3. Haga doble clic en `Button` y agregue el código siguiente al controlador de eventos `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. En el **Explorador de soluciones**, haga clic con el botón derecho en **WindowsApplication1** y haga clic en **Establecer como proyecto de inicio**.

5. Presione **F5** para ejecutar el proyecto. Escriba algún texto y haga clic en el botón. La etiqueta muestra "escribió:" y muestra el texto que escribió.

     ![El formulario que muestra el resultado](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Vea también

- [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
