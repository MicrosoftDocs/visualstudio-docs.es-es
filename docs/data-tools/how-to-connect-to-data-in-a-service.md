---
title: "C&#243;mo: Conectarse a los datos en un servicio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "datos [Visual Studio], conectar con servicios Web"
  - "datos [Visual Studio], leer en servicios Web"
  - "orígenes de datos, crear en servicios Web"
  - "leer datos, en servicios Web"
  - "servicios Web, como orígenes de datos"
  - "servicios Web, conectar"
  - "servicios Web, leer datos"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Conectarse a los datos en un servicio
Se conecta la aplicación a los datos devueltos de un servicio mediante la ejecución del [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) y la selección de la opción **Servicio** de la página **Elegir un tipo de origen de datos**.  
  
 Tras la ejecución correcta del asistente, se agrega una referencia al proyecto que queda inmediatamente disponible en [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
> [!NOTE]
>  Los elementos que aparecen en la ventana **Orígenes de datos** dependen de la información devuelta por el servicio.  Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para la configuración de orígenes de datos** pueda crear objetos enlazables.  Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, ningún elemento aparece en la **Ventana de orígenes de datos** al completar el asistente.  Esto se debe a que los conjuntos de datos sin tipo no proporcionan esquemas; por tanto, el asistente no tiene bastante información para crear el origen de datos.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para conectar la aplicación a un servicio  
  
1.  En el menú **Datos**, haga clic en **Agregar nuevo origen de datos**.  
  
2.  En **Elegir un tipo de origen de datos**, seleccione **Servicio** y, a continuación, haga clic en **Siguiente**.  
  
3.  Escriba la dirección del servicio que desea utilizar o haga clic en **Detectar** para buscar los servicios en la solución actual y, a continuación, haga clic en **Ir**.  
  
4.  Opcionalmente, se puede escribir un nuevo **Espacio de nombres** en lugar del valor predeterminado.  
  
    > [!NOTE]
    >  Haga clic en **Opciones avanzadas** para abrir [Configurar referencia de servicio \(Cuadro de diálogo\)](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Haga clic en **Aceptar** para agregar una referencia del servicio a su proyecto.  
  
6.  Haga clic en **Finalizar**.  
  
     El origen de datos se agrega a la ventana **Orígenes de datos**.  
  
## Pasos siguientes  
  
#### Para agregar funcionalidad a la aplicación  
  
-   Seleccione un elemento en la ventana **Orígenes de datos** y arrástrelo hasta un formulario para crear controles enlazados.  Para obtener más información, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Vea también  
 [Tutorial: Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Tutorial: Enlazar controles de Silverlight a un servicio de datos de WCF](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)