---
title: 'Cómo: Conectarse a los datos en un servicio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f8f7371418df19ec8452334641c7c9414328e557
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305018"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Cómo: Conectarse a los datos en un servicio

Conectar la aplicación a los datos devueltos desde un servicio mediante la ejecución de la [Asistente para configuración de origen de datos](../data-tools/media/data-source-configuration-wizard.png) y seleccionando **servicio** en el **elegir un tipo de origen de datos**página.

Tras la finalización del asistente, se agrega al proyecto una referencia de servicio y esté disponible inmediatamente en el [ventana Orígenes de datos](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Los elementos que aparecen en la ventana Orígenes de datos** dependen de la información devuelta por el servicio. Algunos servicios podrían no proporcionar suficiente información para que el Asistente para la configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, no hay elementos aparecen en la **orígenes de datos** ventana tras la finalización del asistente. Esto es porque los datasets no escritos no proporcionan esquemas, por lo que el asistente no tiene información suficiente para crear el origen de datos.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Para conectar su aplicación a un servicio

1.  En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

2.  Seleccione **servicio** en el **elegir un tipo de origen de datos** página y, a continuación, haga clic en **siguiente**.

3.  Escriba la dirección del servicio que desea usar o haga clic en **Discover** para buscar servicios en la solución actual y, a continuación, haga clic en **vaya**.

4.  Si lo desea, puede escribir un nuevo **Namespace** en lugar del valor predeterminado.

    > [!NOTE]
    > Haga clic en **avanzadas** para abrir el [cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md).

5.  Haga clic en **Aceptar** para agregar una referencia de servicio al proyecto.

6.  Haga clic en **Finalizar**.

     El origen de datos  **se agrega a la ventana Orígenes de datos**.

## <a name="next-steps"></a>Pasos siguientes

Para agregar funcionalidad a la aplicación, seleccione un elemento en el **orígenes de datos** ventana y arrástrelo hasta un formulario para crear controles enlazados. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)