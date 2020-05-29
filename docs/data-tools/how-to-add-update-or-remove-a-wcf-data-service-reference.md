---
title: 'Cómo: Agregar, actualizar o quitar una referencia de servicio de datos de WCF'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 494e85049a173749d418276340389ebe826a0b0b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184241"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedimiento para agregar, actualizar o eliminar una referencia de servicio de datos WCF

::: moniker range="vs-2017"
Una *referencia de servicio* permite a un proyecto tener acceso a uno o varios [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] . Utilice el cuadro de diálogo **Agregar referencia de servicio** para buscar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en la solución actual, localmente, en una red de área local o en Internet.
::: moniker-end
::: moniker range=">=vs-2019"
Puede usar el nodo **servicios conectados** en **Explorador de soluciones** para tener acceso a la **Microsoft WCF Web Service Reference Provider**, que le permite administrar las referencias del servicio de datos Windows Communication Foundation (WCF).
::: moniker-end

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-wcf-service-reference"></a>Agregar una referencia de servicio WCF

### <a name="to-add-a-reference-to-an-external-service"></a>Para agregar una referencia a un servicio externo

::: moniker range="vs-2017"

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto al que desea agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.

   Aparecerá el cuadro de diálogo **Agregar referencia de servicio**.

1. En el cuadro **Dirección** , escriba la dirección URL del servicio y, a continuación, haga clic en **ir** para buscar el servicio. Si el servicio implementa la seguridad de nombre de usuario y contraseña, es posible que se le pida un nombre de usuario y una contraseña.

    > [!NOTE]
    > Solo debe hacer referencia a servicios desde un origen de confianza. Si agrega referencias desde un origen que no es de confianza podría poner en peligro la seguridad.

     También puede seleccionar la dirección URL de la lista de **direcciones** , que almacena las 15 direcciones URL anteriores en las que se encontraron los metadatos de servicio válidos.

     Se muestra una barra de progreso cuando se realiza la búsqueda. Para detener la búsqueda en cualquier momento, haga clic en **detener**.

1. En la lista de **servicios** , expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.

1. En el cuadro **Espacio de nombres**, especifique el espacio de nombres que desea usar para la referencia.

1. Haga clic en **Aceptar** para agregar la referencia al proyecto.

     Se genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan al archivo *app. config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. En **Explorador de soluciones**, haga doble clic en el nodo **servicios conectados** o Púlselo.

   Se abre la pestaña **configurar servicios** .

1. Elija **Microsoft WCF Web Service Reference Provider**.

   Aparecerá el cuadro de diálogo **configurar referencia de servicio Web WCF** .

   ![Captura de pantalla del cuadro de diálogo proveedor de servicios Web WCF](media/vs-2019/configure-wcf-web-service-reference-dialog.png)


1. En el cuadro **URI** , escriba la dirección URL del servicio y, a continuación, haga clic en **ir** para buscar el servicio. Si el servicio implementa la seguridad de nombre de usuario y contraseña, es posible que se le pida un nombre de usuario y una contraseña.

    > [!NOTE]
    > Solo debe hacer referencia a servicios desde un origen de confianza. Si agrega referencias desde un origen que no es de confianza podría poner en peligro la seguridad.

     También puede seleccionar la dirección URL de la lista **URI** , que almacena las 15 direcciones URL anteriores en las que se encontraron los metadatos de servicio válidos.

     Se muestra una barra de progreso cuando se realiza la búsqueda. Para detener la búsqueda en cualquier momento, haga clic en **detener**.

1. En la lista de **servicios** , expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.

1. En el cuadro **Espacio de nombres**, especifique el espacio de nombres que desea usar para la referencia.

1. Haga clic en **Finalizar** para agregar la referencia al proyecto.

     Se genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan al archivo *app. config* .

::: moniker-end

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para agregar una referencia a un servicio en la solución actual

::: moniker range="vs-2017"

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto al que desea agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.

    Aparecerá el cuadro de diálogo **Agregar referencia de servicio**.

1. Haga clic en **detectar**.

    Todos los servicios ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] y servicios WCF) de la solución actual se agregan a la lista de **servicios** .

1. En la lista de **servicios** , expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.

1. En el cuadro **Espacio de nombres**, especifique el espacio de nombres que desea usar para la referencia.

1. Haga clic en **Aceptar** para agregar la referencia al proyecto.

    Un cliente de servicio (proxy) genera, y los metadatos que describen el servicio se agregan al archivo *app. config* .
::: moniker-end
::: moniker range=">=vs-2019"
1. En **Explorador de soluciones**, haga doble clic en el nodo **servicios conectados** o Púlselo. 

   Se abre la pestaña **configurar servicios** .

1. Elija **Microsoft WCF Web Service Reference Provider**.

   Aparecerá el cuadro de diálogo **configurar referencia de servicio Web WCF** .

1. Haga clic en **detectar**.

    Todos los servicios ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] y servicios WCF) de la solución actual se agregan a la lista de **servicios** .

1. En la lista de **servicios** , expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.

1. En el cuadro **Espacio de nombres**, especifique el espacio de nombres que desea usar para la referencia.

1. Haga clic en **Finalizar** para agregar la referencia al proyecto.

    Un cliente de servicio (proxy) genera, y los metadatos que describen el servicio se agregan al archivo *app. config* .

::: moniker-end

## <a name="update-a-service-reference"></a>Actualizar una referencia de servicio

A veces, el Entity Data Model para un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] cambia. Cuando esto sucede, debe actualizar la referencia de servicio.

### <a name="to-update-a-service-reference"></a>Para actualizar una referencia de servicio

- En **Explorador de soluciones**, haga clic con el botón secundario en la referencia de servicio y, a continuación, haga clic en **Actualizar referencia de servicio**.

     Se muestra un cuadro de diálogo de progreso mientras la referencia se actualiza desde su ubicación original, y el cliente del servicio se regenera para reflejar los cambios en los metadatos.

## <a name="remove-a-service-reference"></a>Quitar una referencia de servicio

Si ya no se usa una referencia de servicio, puede quitarla de la solución.

### <a name="to-remove-a-service-reference"></a>Para quitar una referencia de servicio

- En **Explorador de soluciones**, haga clic con el botón secundario en la referencia de servicio y, a continuación, haga clic en **eliminar**.

     El cliente del servicio se quitará de la solución y los metadatos que describen el servicio se quitarán del archivo *app. config* .

    > [!NOTE]
    > Cualquier código que haga referencia a la referencia de servicio debe quitarse manualmente.

## <a name="see-also"></a>Consulta también

- [Servicios de Windows Communication Foundation y servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
