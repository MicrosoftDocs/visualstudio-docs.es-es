---
title: 'Tutorial: Crear un servicio WCF sencillo en Windows Forms | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e14944157a14be4a5e06c26464a4de2cdb2bff1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567668"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Tutorial: Crear un servicio WCF sencillo en Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: crear un servicio WCF sencillo en Windows Forms](https://docs.microsoft.com/visualstudio/data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms).  
  
  
Este tutorial muestra cómo se crea un sencillo servicio de [!INCLUDE[vsindigo](../includes/vsindigo-md.md)]. A continuación, se probará y se tendrá acceso a él desde una aplicación de Windows Forms.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>Crear el servicio web  
  
#### <a name="to-create-a-wcf-service"></a>Para crear un servicio WCF  
  
1.  En el menú **Archivo** , elija **Nuevo** y haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** nodo y haga clic en **WCF**, seguido de **WCF Biblioteca de servicios de**. Haga clic en **Aceptar** para abrir el proyecto.  
  
     ![El proyecto de biblioteca de servicios WCF](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  Se creará un servicio de trabajo que puede probar y acceder a él. Los dos pasos siguientes muestran cómo puede modificar el método predeterminado para utilizar un tipo de datos diferente. En una aplicación real, también agregaría sus propias funciones al servicio.  
  
3.  ![El archivo IService1](../data-tools/media/wcf2.png "wcf2")  
  
     En **el Explorador de soluciones**, haga doble clic en IService1.vb o IService1.cs y busque la línea siguiente:  
  
     [! código csharp [WCFWalkthrough #4] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/CS/IService1 (2).cs 4)] [! código vb [WCFWalkthrough #4] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/IService1 (2).vb 4)]  
  
     Cambiar el tipo del parámetro `value` a `String`:  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     En el código anterior, observe los atributos `<OperationContract()>` o `[OperationContract]`. Estos atributos son obligatorios para cualquier método expuesto por el servicio.  
  
4.  ![El archivo Service1](../data-tools/media/wcf3.png "wcf3")  
  
     En **el Explorador de soluciones**, haga doble clic en Service1.vb o Service1.cs y busque la línea siguiente:  
  
     [! código csharp [WCFWalkthrough 5] (.. /Snippets/CSharp/VS_Snippets_VBCSharp/wcfwalkthrough/CS/Service1 (2).cs Nº 5)] [! código vb [WCFWalkthrough 5] (.. /Snippets/VisualBasic/VS_Snippets_VBCSharp/wcfwalkthrough/VB/Service1 (2).vb Nº 5)]  
  
     Cambiar el tipo del parámetro de valor a `String`:  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>Probar el servicio  
  
#### <a name="to-test-a-wcf-service"></a>Para probar un servicio WCF  
  
1.  Presione **F5** para ejecutar el servicio. Un **cliente de prueba WCF** se mostrará el formulario y cargará el servicio.  
  
2.  En el **cliente de prueba WCF** formulario, haga doble clic en el **GetData()** método sometido a **IService1**. El **GetData** se mostrará la pestaña.  
  
     ![El método GetData&#40; &#41; método](../data-tools/media/wcf4.png "wcf4")  
  
3.  En el **solicitar** cuadro, seleccione el **valor** campo y el tipo `Hello`.  
  
     ![El campo de valor](../data-tools/media/wcf5.png "wcf5")  
  
4.  Haga clic en el **Invoke** botón. Si un **advertencia de seguridad** se muestra el cuadro de diálogo, haga clic en **Aceptar**. El resultado se mostrará en el **respuesta** cuadro.  
  
     ![El resultado en el cuadro respuesta](../data-tools/media/wcf6.png "wcf6")  
  
5.  En el **archivo** menú, haga clic en **Exit** para cerrar el formulario de prueba.  
  
## <a name="accessing-the-service"></a>Acceso al servicio  
  
#### <a name="to-reference-a-wcf-service"></a>Para hacer referencia a un servicio WCF  
  
1.  En el **archivo** menú, elija **agregar** y, a continuación, haga clic en **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual Basic** o **Visual C#** nodo y seleccione **Windows**y, a continuación, seleccione **Aplicación de Windows Forms**. Haga clic en **Aceptar** para abrir el proyecto.  
  
     ![Proyecto de aplicación de Windows Forms](../data-tools/media/wcf7.png "wcf7")  
  
3.  Haga clic en **WindowsApplication1** y haga clic en **Add Service Reference**. El **Add Service Reference** aparecerá el cuadro de diálogo.  
  
4.  En el **Add Service Reference** cuadro de diálogo, haga clic en **Discover**.  
  
     ![El cuadro de diálogo Agregar referencia de servicio](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1** se mostrará en el **servicios** panel.  
  
5.  Haga clic en **Aceptar** para agregar la referencia de servicio.  
  
#### <a name="to-build-a-client-application"></a>Para compilar una aplicación cliente  
  
1.  En **el Explorador de soluciones**, haga doble clic en **Form1.vb** o **Form1.cs** para abrir el Diseñador de formularios de Windows si no está ya abierto.  
  
2.  Desde el **cuadro de herramientas**, arrastre un `TextBox` (control), un `Label` control y un `Button` al formulario.  
  
     ![Agregar controles al formulario](../data-tools/media/wcf9.png "wcf9")  
  
3.  Haga doble clic en `Button` y agregue el código siguiente al controlador de eventos `Click`:  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  En **el Explorador de soluciones**, haga clic en **WindowsApplication1** y haga clic en **establecer como proyecto de inicio**.  
  
5.  Presione **F5** para ejecutar el proyecto. Escriba algún texto y haga clic en el botón. La etiqueta mostrará "Escribió:" y el texto que escribió.  
  
     ![El formulario que muestra el resultado](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>Vea también  
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

