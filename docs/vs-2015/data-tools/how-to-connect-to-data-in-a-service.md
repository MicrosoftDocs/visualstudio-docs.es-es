---
title: Procedimiento Conectarse a datos en un servicio | Documentos de Microsoft
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
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 22a1a991a950ba8e1a7c4c39299616641797630c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684739"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedimiento Conexión a los datos en un servicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Conectar la aplicación a los datos devueltos desde un servicio mediante la ejecución de la [Asistente para configuración de origen de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) y seleccionando **servicio** en el **elegir un tipo de origen de datos**página.  
  
 Tras la finalización del asistente, se agrega al proyecto una referencia de servicio y esté disponible inmediatamente en el [ventana Orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
> Los elementos que aparecen en la ventana **Orígenes de datos** dependen de la información devuelta por el servicio. Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, a continuación, no hay elementos aparecen en la **ventana Orígenes de datos** al finalizar el asistente. Esto es porque los datasets no escritos no proporcionan esquemas, por lo que el asistente no tiene información suficiente para crear el origen de datos.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Para conectar su aplicación a un servicio  
  
1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.  
  
2. Seleccione **servicio** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.  
  
3. Escriba la dirección del servicio que desea usar o haga clic en **Discover** para buscar servicios en la solución actual y, a continuación, haga clic en **vaya**.  
  
4. Opcionalmente, un nuevo **Namespace** pueden escribirse en lugar del valor predeterminado.  
  
    > [!NOTE]
    > Haga clic en **avanzadas** para abrir el [cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md).  
  
5. Haga clic en **Aceptar** para agregar una referencia de servicio al proyecto.  
  
6. Haga clic en **Finalizar**.  
  
     El origen de datos se agrega a la ventana **Orígenes de datos**.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
#### <a name="to-add-functionality-to-your-application"></a>Para agregar funcionalidad a la aplicación  
  
- Seleccione un elemento en el **orígenes de datos** ventana y arrástrelo hasta un formulario para crear controles enlazados. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles WPF a WCF data Services](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
