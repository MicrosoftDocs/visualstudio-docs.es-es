---
title: 'Cómo: conectarse a los datos de un servicio | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654686"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Cómo: Conectarse a los datos en un servicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Conecte la aplicación a los datos devueltos desde un servicio ejecutando el [Asistente para la configuración de orígenes de datos](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) y seleccionando **servicio** en la página **elegir un tipo de origen de datos** .

 Al finalizar el asistente, se agrega una referencia de servicio al proyecto y está inmediatamente disponible en la [ventana orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

> [!NOTE]
> Los elementos que aparecen en la ventana **Orígenes de datos** dependen de la información devuelta por el servicio. Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para configuración de orígenes de datos** pueda crear objetos enlazables. Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, en la **ventana orígenes de datos** no aparece ningún elemento cuando se completa el asistente. Esto se debe a que los conjuntos de datos sin tipo no proporcionan el esquema, por lo que el asistente no tiene suficiente información para crear el origen de datos.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Para conectar la aplicación a un servicio

1. En el menú **Datos** , haga clic en **Agregar nuevo elemento**.

2. Seleccione **servicio** en la página **elegir un tipo de origen de datos** y, a continuación, haga clic en **siguiente**.

3. Escriba la dirección del servicio que quiere usar o haga clic en **detectar** para buscar servicios en la solución actual y, a continuación, haga clic en **ir**.

4. Opcionalmente, se puede escribir un nuevo **espacio de nombres** en lugar del valor predeterminado.

    > [!NOTE]
    > Haga clic en **avanzadas** para abrir el [cuadro de diálogo Configurar referencia de servicio](../data-tools/configure-service-reference-dialog-box.md).

5. Haga clic en **Aceptar** para agregar una referencia de servicio al proyecto.

6. Haga clic en **Finalizar**

     El origen de datos se agrega a la ventana **Orígenes de datos**.

## <a name="next-steps"></a>Pasos siguientes

#### <a name="to-add-functionality-to-your-application"></a>Para agregar funcionalidad a la aplicación

- Seleccione un elemento de la ventana **orígenes de datos** y arrástrelo hasta un formulario para crear controles enlazados. Para obtener más información, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
 [Enlazar controles de WPF a un servicio de datos de WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Windows Communication Foundation servicios y WCF Data Services en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
