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
ms.openlocfilehash: c60dffc7bb47336ae36e64a366def3c4dce06213
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586593"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Procedimiento para agregar, actualizar o eliminar una referencia de servicio de datos WCF
Una *referencia de servicio* permite a un proyecto tener acceso a uno o más [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Utilice el cuadro de diálogo **Agregar referencia de servicio** para buscar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en la solución actual, localmente, en una red de área local o en Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Agregar una referencia de servicio

### <a name="to-add-a-reference-to-an-external-service"></a>Para agregar una referencia a un servicio externo

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto al que desea agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.

     Aparece el cuadro de diálogo **Agregar referencia de servicio** .

2. En el cuadro **Dirección** , escriba la dirección URL del servicio y, a continuación, haga clic en **ir** para buscar el servicio. Si el servicio implementa la seguridad de nombre de usuario y contraseña, es posible que se le pida un nombre de usuario y una contraseña.

    > [!NOTE]
    > Solo debe hacer referencia a servicios desde un origen de confianza. Si agrega referencias desde un origen que no es de confianza podría poner en peligro la seguridad.

     También puede seleccionar la dirección URL de la lista de **direcciones** , que almacena las 15 direcciones URL anteriores en las que se encontraron los metadatos de servicio válidos.

     Se muestra una barra de progreso cuando se realiza la búsqueda. Para detener la búsqueda en cualquier momento, haga clic en **detener**.

3. En la lista de **servicios** , expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.

4. En el cuadro **espacio de nombres** , escriba el espacio de nombres que desea utilizar para la referencia.

5. Haga clic en **Aceptar** para agregar la referencia al proyecto.

     Se genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan al archivo *app. config* .

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para agregar una referencia a un servicio en la solución actual

1. En **Explorador de soluciones**, haga clic con el botón secundario en el nombre del proyecto al que desea agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.

    Aparece el cuadro de diálogo **Agregar referencia de servicio** .

2. Haga clic en **detectar**.

    Todos los servicios ([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] y servicios WCF) de la solución actual se agregan a la lista de **servicios** .

3. En la lista de **servicios** , expanda el nodo del servicio que desea usar y seleccione un conjunto de entidades.

4. En el cuadro **espacio de nombres** , escriba el espacio de nombres que desea utilizar para la referencia.

5. Haga clic en **Aceptar** para agregar la referencia al proyecto.

    Un cliente de servicio (proxy) genera, y los metadatos que describen el servicio se agregan al archivo *app. config* .

## <a name="update-a-service-reference"></a>Actualizar una referencia de servicio
A veces, el Entity Data Model de una [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] cambia. Cuando esto sucede, debe actualizar la referencia de servicio.

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

## <a name="see-also"></a>Vea también

- [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
