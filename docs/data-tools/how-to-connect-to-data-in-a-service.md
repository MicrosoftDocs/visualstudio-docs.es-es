---
title: 'Cómo: Conectarse a los datos en un servicio'
description: Conecte la aplicación a los datos devueltos por un servicio ejecutando el Asistente para la configuración de orígenes de datos y seleccionando servicio en la página elegir un tipo de origen de datos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c565f7238edf9126dd651fa567de82aed7b8d21
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435018"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Procedimiento para conectarse a datos de un servicio

Conecte la aplicación a los datos devueltos desde un servicio ejecutando el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) y seleccionando **servicio** en la página **elegir un tipo de origen de datos** .

Al finalizar el asistente, se agrega una referencia de servicio al proyecto y está inmediatamente disponible en la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Los elementos que aparecen en la ventana **Orígenes de datos** dependen de la información devuelta por el servicio. Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, en la ventana **orígenes de datos** no aparece ningún elemento cuando se completa el asistente. Esto se debe a que los conjuntos de datos sin tipo no proporcionan el esquema, por lo que el asistente no tiene suficiente información para crear el origen de datos.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Para conectar la aplicación a un servicio

1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

2. Seleccione **servicio** en la página **elegir un tipo de origen de datos** y, a continuación, haga clic en **siguiente**.

3. Escriba la dirección del servicio que quiere usar o haga clic en **detectar** para buscar servicios en la solución actual y, a continuación, haga clic en **ir**.

4. Opcionalmente, puede escribir un nuevo **espacio de nombres** en lugar del valor predeterminado.

    > [!NOTE]
    > Haga clic en **avanzadas** para abrir el [cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md).

5. Haga clic en **Aceptar** para agregar una referencia de servicio al proyecto.

6. Haga clic en **Finalizar**

     El origen de datos se agrega a la ventana **Orígenes de datos**.

## <a name="next-steps"></a>Pasos siguientes

Para agregar funcionalidad a la aplicación, seleccione un elemento en la ventana **orígenes de datos** y arrástrelo hasta un formulario para crear controles enlazados. Para obtener más información, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Consulte también

- [Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Servicios de Windows Communication Foundation y servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
