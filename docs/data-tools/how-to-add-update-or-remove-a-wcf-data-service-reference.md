---
title: "Cómo: agregar, actualizar o quitar una referencia de servicio de datos WCF | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c35fdaabf3de306af0541fb4781a085a3c409ff8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Cómo: Agregar, actualizar o quitar una referencia de servicio de datos de WCF
A *referencia de servicio* permite a un proyecto para tener acceso a uno o más [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Use la **Agregar referencia de servicio** cuadro de diálogo para buscar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en la solución actual, localmente, en una red de área local o en Internet.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-a-service-reference"></a>Agregar una referencia de servicio  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Para agregar una referencia a un servicio externo  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto que desea agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.  
  
     El **Agregar referencia de servicio** aparece el cuadro de diálogo.  
  
2.  En el **dirección** cuadro, escriba la dirección URL para el servicio y, a continuación, haga clic en **vaya** para buscar el servicio. Si el servicio implementa seguridad de nombre y la contraseña de usuario, se le pedirá un nombre de usuario y una contraseña.  
  
    > [!NOTE]
    >  Solo debe hacer referencia a servicios desde un origen de confianza. Agregar referencias de un origen de confianza puede poner en peligro la seguridad.  
  
     También puede seleccionar la dirección URL de la **dirección** lista, que almacena las 15 direcciones URL anteriores a la que se encontraron metadatos de servicio válida.  
  
     Una barra de progreso se muestra cuando se realiza la búsqueda. Puede detener la búsqueda en cualquier momento haciendo clic en **detener**.  
  
3.  En el **servicios** lista, expanda el nodo para el servicio que desea usar y seleccione un conjunto de entidades.  
  
4.  En el **Namespace** cuadro, escriba el espacio de nombres que desea usar para la referencia.  
  
5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.  
  
     Se genera un cliente de servicio (proxy) y metadatos que describen el servicio se agregan al archivo app.config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para agregar una referencia a un servicio en la solución actual  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto que desea agregar el servicio y, a continuación, haga clic en **Agregar referencia de servicio**.  
  
     El **Agregar referencia de servicio** aparece el cuadro de diálogo.  
  
2.  Haga clic en **detectar**.  
  
     Todos los servicios (ambos [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] y servicios de WCF) en la solución actual se agregan a la **servicios** lista.  
  
3.  En el **servicios** lista, expanda el nodo para el servicio que desea usar y seleccione un conjunto de entidades.  
  
4.  En el **Namespace** cuadro, escriba el espacio de nombres que desea usar para la referencia.  
  
5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.  
  
     Se genera un cliente de servicio (proxy) y metadatos que describen el servicio se agregan al archivo app.config.  
  
## <a name="updating-a-service-reference"></a>Actualizar una referencia de servicio  
 Entity Data Model para un [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] a veces cambiará. Cuando esto sucede, debe actualizarse la referencia de servicio.  
  
#### <a name="to-update-a-service-reference"></a>Para actualizar una referencia de servicio  
  
-   En **el Explorador de soluciones**, haga clic en la referencia de servicio y, a continuación, haga clic en **Actualizar referencia de servicio**.  
  
     Se muestra un cuadro de diálogo de progreso mientras la referencia se actualiza desde su ubicación original y el cliente del servicio se vuelve a generar para reflejar los cambios en los metadatos.  
  
## <a name="removing-a-service-reference"></a>Quitar una referencia de servicio  
 Si ya no se utiliza una referencia de servicio, puede quitarlo de la solución.  
  
#### <a name="to-remove-a-service-reference"></a>Para quitar una referencia de servicio  
  
-   En **el Explorador de soluciones**, haga clic en la referencia de servicio y, a continuación, haga clic en **eliminar**.  
  
     El cliente del servicio se quitará de la solución y los metadatos que describen el servicio se quitarán del archivo app.config.  
  
    > [!NOTE]
    >  Cualquier código que hace referencia a la referencia de servicio debe quitarse manualmente.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)