---
title: 'Cómo: Conectarse a los datos en un servicio'
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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d6f90a99a387452500686af332edb1d112a88f82
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089123"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Cómo: conectarse a datos en un servicio

Conectar la aplicación a los datos devueltos desde un servicio mediante la ejecución de la [Asistente para configuración de origen de datos](../data-tools/media/data-source-configuration-wizard.png) y seleccionando **servicio** en el **elegir un tipo de origen de datos**página.

Tras la finalización del asistente, se agrega al proyecto una referencia de servicio y esté disponible inmediatamente en el [ventana Orígenes de datos](add-new-data-sources.md).

> [!NOTE]
> Los elementos que aparecen en la **orígenes de datos** ventana dependen de la información que devuelve el servicio. Algunos servicios podrían no proporcionar suficiente información para el **Asistente para configuración de origen de datos** para crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, no hay elementos aparecen en la **ventana Orígenes de datos** al finalizar el asistente. Esto es porque los datasets no escritos no proporcionan esquemas, por lo que el asistente no tiene información suficiente para crear el origen de datos.

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

     El origen de datos se agrega a la **orígenes de datos** ventana.

## <a name="next-steps"></a>Pasos siguientes

Para agregar funcionalidad a la aplicación, seleccione un elemento en el **orígenes de datos** ventana y arrástrelo hasta un formulario para crear controles enlazados. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servicios de datos de servicios de Windows Communication Foundation y WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)