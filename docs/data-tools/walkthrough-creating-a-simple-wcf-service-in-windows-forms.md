---
title: 'Tutorial: Crear un servicio WCF sencillo en Windows Forms'
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e2c9d0bd58adcd0a0595c061fa4dfaa81f629601
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174252"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Tutorial: Crear un servicio WCF sencillo en Windows Forms

Este tutorial muestra cómo se crea un sencillo servicio de [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]. A continuación, se probará y se tendrá acceso a él desde una aplicación de Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Crear el servicio

### <a name="to-create-a-wcf-service"></a>Para crear un servicio WCF

1.  En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.

2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** nodo y haga clic en **WCF**, seguido de **WCF Biblioteca de servicios de**. Haga clic en **Aceptar** para abrir el proyecto.

     ![El proyecto de biblioteca de servicios de WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Se creará un servicio de trabajo que puede probar y acceder a él. Los dos pasos siguientes muestran cómo puede modificar el método predeterminado para utilizar un tipo de datos diferente. En una aplicación real, también agregaría sus propias funciones al servicio.

3.  ![El archivo IService1](../data-tools/media/wcf2.png)

     En **el Explorador de soluciones**, haga doble clic en **IService1.vb** o **IService1.cs** y busque la línea siguiente:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Cambiar el tipo de la `value` parámetro de cadena:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     En el código anterior, observe los atributos `<OperationContract()>` o `[OperationContract]`. Estos atributos son obligatorios para cualquier método expuesto por el servicio.

4.  ![El archivo Service1](../data-tools/media/wcf3.png)

     En **el Explorador de soluciones**, haga doble clic en **Service1.vb** o **Service1.cs** y busque la línea siguiente:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Cambiar el tipo de la `value` parámetro de cadena:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Probar el servicio

### <a name="to-test-a-wcf-service"></a>Para probar un servicio WCF

1.  Presione **F5** para ejecutar el servicio. Un **cliente de prueba WCF** el formulario aparece y carga el servicio.

2.  En el **cliente de prueba WCF** formulario, haga doble clic en el **GetData()** método sometido a **IService1**. El **GetData** aparecerá la pestaña.

     ![El método GetData&#40; &#41; (método)](../data-tools/media/wcf4.png)

3.  En el **solicitar** cuadro, seleccione el **valor** campo y el tipo `Hello`.

     ![El campo Valor](../data-tools/media/wcf5.png)

4.  Haga clic en el **Invoke** botón. Si un **advertencia de seguridad** aparece el cuadro de diálogo, haga clic en **Aceptar**. El resultado se muestra en el **respuesta** cuadro.

     ![El resultado en el cuadro Respuesta](../data-tools/media/wcf6.png)

5.  En el **archivo** menú, haga clic en **Exit** para cerrar el formulario de prueba.

## <a name="access-the-service"></a>Obtener acceso al servicio

### <a name="to-reference-a-wcf-service"></a>Para hacer referencia a un servicio WCF

1.  En el **archivo** menú, elija **agregar** y, a continuación, haga clic en **nuevo proyecto**.

2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** nodo, seleccione **Windows**y, a continuación, seleccione  **Aplicación de Windows Forms**. Haga clic en **Aceptar** para abrir el proyecto.

     ![Proyecto de Aplicación de Windows Forms](../data-tools/media/wcf7.png)

3.  Haga clic en **WindowsApplication1** y haga clic en **Add Service Reference**. El **Add Service Reference** aparece el cuadro de diálogo.

4.  En el **Add Service Reference** cuadro de diálogo, haga clic en **Discover**.

     ![El cuadro de diálogo Agregar referencia de servicio](../data-tools/media/wcf8.png)

     **Service1** se muestra en el **servicios** panel.

5.  Haga clic en **Aceptar** para agregar la referencia de servicio.

### <a name="to-build-a-client-application"></a>Para compilar una aplicación cliente

1.  En **el Explorador de soluciones**, haga doble clic en **Form1.vb** o **Form1.cs** para abrir el Diseñador de formularios de Windows si no está ya abierto.

2.  Desde el **cuadro de herramientas**, arrastre un `TextBox` (control), un `Label` control y un `Button` al formulario.

     ![Agregar controles al formulario](../data-tools/media/wcf9.png)

3.  Haga doble clic en `Button` y agregue el código siguiente al controlador de eventos `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  En **el Explorador de soluciones**, haga clic en **WindowsApplication1** y haga clic en **establecer como proyecto de inicio**.

5.  Presione **F5** para ejecutar el proyecto. Escriba algún texto y haga clic en el botón. Muestra la etiqueta "escribió:" y se muestra el texto que escribió.

     ![El formulario que muestra el resultado](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Vea también

- [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)