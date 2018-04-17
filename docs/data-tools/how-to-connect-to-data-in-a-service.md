---
title: 'Cómo: conectarse a los datos en un servicio | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6e85af7411da7ff9f7912c4127d51db100f82063
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-connect-to-data-in-a-service"></a>Cómo: Conectarse a los datos en un servicio
Conectar su aplicación a los datos devueltos desde un servicio mediante la ejecución de la [Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) y seleccionando **servicio** en el **elegir un tipo de origen de datos**página.  
  
 Tras la finalización del asistente, se agrega al proyecto una referencia de servicio y está disponible de inmediato en el [ventana Orígenes de datos](add-new-data-sources.md).  
  
> [!NOTE]
>  Los elementos que aparecen en la **orígenes de datos** ventana dependen de la información devuelta por el servicio. Algunos servicios podrían no proporcionar suficiente información para que la **Data Source Configuration Wizard** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, a continuación, no aparece ningún elemento en el **ventana Orígenes de datos** al finalizar el asistente. Esto es porque los conjuntos de datos sin tipo no proporcionan esquemas, por lo que el asistente no tiene información suficiente para crear el origen de datos.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Para conectar su aplicación a un servicio  
  
1.  En el menú **Datos** , haga clic en **Agregar nuevo elemento**.  
  
2.  Seleccione **servicio** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.  
  
3.  Escriba la dirección del servicio que desea usar o haga clic en **Discover** para buscar servicios en la solución actual y, a continuación, haga clic en **vaya**.  
  
4.  Si lo desea, un nuevo **Namespace** pueden escribirse en lugar del valor predeterminado.  
  
    > [!NOTE]
    >  Haga clic en **avanzadas** para abrir el [cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Haga clic en **Aceptar** para agregar una referencia de servicio a su proyecto.  
  
6.  Haga clic en **Finalizar**.  
  
     El origen de datos se agrega a la **orígenes de datos** ventana.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
#### <a name="to-add-functionality-to-your-application"></a>Para agregar funcionalidad a la aplicación  
  
-   Seleccione un elemento en el **orígenes de datos** ventana y arrástrelo hasta un formulario para crear controles enlazados. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles WPF a un servicio de datos WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)