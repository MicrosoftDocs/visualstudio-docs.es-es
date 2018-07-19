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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b6726b2c859143f5dbc9b264e67bb9bb91757de5
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089317"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Cómo: agregar, actualizar o quitar una referencia de servicio de datos WCF
Un *referencia de servicio* habilita a un proyecto para tener acceso a uno o más [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Use la **Add Service Reference** cuadro de diálogo para buscar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en la solución actual, localmente, en una red de área local o en Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Agregar una referencia de servicio

### <a name="to-add-a-reference-to-an-external-service"></a>Para agregar una referencia a un servicio externo

1.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto al que desea agregar el servicio y, a continuación, haga clic en **Add Service Reference**.

     El **Add Service Reference** aparece el cuadro de diálogo.

2.  En el **dirección** cuadro, escriba la dirección URL del servicio y, a continuación, haga clic en **vaya** para buscar el servicio. Si el servicio implementa seguridad de nombre y la contraseña de usuario, se le pedirá un nombre de usuario y contraseña.

    > [!NOTE]
    >  Solo debe hacer referencia a servicios desde un origen de confianza. Si agrega referencias desde un origen que no es de confianza podría poner en peligro la seguridad.

     También puede seleccionar la dirección URL de la **dirección** lista, que almacena las 15 direcciones URL anteriores a la que se encontraron metadatos de servicio válido.

     Una barra de progreso se muestra cuando se realiza la búsqueda. Puede detener la búsqueda en cualquier momento haciendo **detener**.

3.  En el **servicios** lista, expanda el nodo para el servicio que desea usar y seleccione un conjunto de entidades.

4.  En el **Namespace** , escriba el espacio de nombres que desea usar para la referencia.

5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.

     Se genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan a la *app.config* archivo.

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para agregar una referencia a un servicio en la solución actual

1.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto al que desea agregar el servicio y, a continuación, haga clic en **Add Service Reference**.

     El **Add Service Reference** aparece el cuadro de diálogo.

2.  Haga clic en **detectar**.

     Todos los servicios (ambos [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] y los servicios de WCF) en la solución actual se agregan a la **servicios** lista.

3.  En el **servicios** lista, expanda el nodo para el servicio que desea usar y seleccione un conjunto de entidades.

4.  En el **Namespace** , escriba el espacio de nombres que desea usar para la referencia.

5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.

     Genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan a la *app.config* archivo.

## <a name="update-a-service-reference"></a>Actualizar una referencia de servicio
 El Entity Data Model para un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] a veces cambia. Cuando esto sucede, debe actualizar la referencia de servicio.

### <a name="to-update-a-service-reference"></a>Para actualizar una referencia de servicio

-   En **el Explorador de soluciones**, haga clic en la referencia de servicio y, a continuación, haga clic en **Actualizar referencia de servicio**.

     Un cuadro de diálogo de progreso se muestra mientras se actualiza la referencia de su ubicación original, y el cliente del servicio se vuelve a generar para reflejar los cambios en los metadatos.

## <a name="remove-a-service-reference"></a>Quitar una referencia de servicio
 Si ya no se utiliza una referencia de servicio, puede quitarlo de la solución.

### <a name="to-remove-a-service-reference"></a>Para quitar una referencia de servicio

-   En **el Explorador de soluciones**, haga clic en la referencia de servicio y, a continuación, haga clic en **eliminar**.

     El cliente del servicio se quitará de la solución y los metadatos que describen el servicio se quitará el *app.config* archivo.

    > [!NOTE]
    >  Cualquier código que hace referencia a la referencia de servicio debe quitarse manualmente.

## <a name="see-also"></a>Vea también

- [Servicios de datos de servicios de Windows Communication Foundation y WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)