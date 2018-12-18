---
title: 'Cómo: agregar, actualizar o quitar una referencia de servicio de datos WCF | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b14a83b195809dff89fa89bb6fcf91050e2f8a0c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192262"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Cómo: Agregar, actualizar o quitar una referencia de servicio de datos de WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Un *referencia de servicio* habilita a un proyecto para tener acceso a uno o más [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]. Use la **Add Service Reference** cuadro de diálogo para buscar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] en la solución actual, localmente, en una red de área local o en Internet.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-a-service-reference"></a>Agregar una referencia de servicio  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Para agregar una referencia a un servicio externo  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto que desea agregar el servicio y, a continuación, haga clic en **Add Service Reference**.  
  
     El **Add Service Reference** aparece el cuadro de diálogo.  
  
2.  En el **dirección** cuadro, escriba la dirección URL del servicio y, a continuación, haga clic en **vaya** para buscar el servicio. Si el servicio implementa seguridad de nombre y la contraseña de usuario, se le pedirá un nombre de usuario y contraseña.  
  
    > [!NOTE]
    >  Solo debe hacer referencia a servicios desde un origen de confianza. Si agrega referencias desde un origen que no es de confianza podría poner en peligro la seguridad.  
  
     También puede seleccionar la dirección URL de la **dirección** lista, que almacena las 15 direcciones URL anteriores a la que se encontraron metadatos de servicio válido.  
  
     Una barra de progreso se muestra cuando se realiza la búsqueda. Puede detener la búsqueda en cualquier momento haciendo **detener**.  
  
3.  En el **servicios** lista, expanda el nodo para el servicio que desea usar y seleccione un conjunto de entidades.  
  
4.  En el **Namespace** , escriba el espacio de nombres que desea usar para la referencia.  
  
5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.  
  
     Se genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan al archivo app.config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para agregar una referencia a un servicio en la solución actual  
  
1.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto que desea agregar el servicio y, a continuación, haga clic en **Add Service Reference**.  
  
     El **Add Service Reference** aparece el cuadro de diálogo.  
  
2.  Haga clic en **detectar**.  
  
     Todos los servicios (ambos [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] y los servicios de WCF) en la solución actual se agregan a la **servicios** lista.  
  
3.  En el **servicios** lista, expanda el nodo para el servicio que desea usar y seleccione un conjunto de entidades.  
  
4.  En el **Namespace** , escriba el espacio de nombres que desea usar para la referencia.  
  
5.  Haga clic en **Aceptar** para agregar la referencia al proyecto.  
  
     Se genera un cliente de servicio (proxy) y los metadatos que describen el servicio se agregan al archivo app.config.  
  
## <a name="updating-a-service-reference"></a>Actualizar una referencia de servicio  
 El Entity Data Model para un [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] cambiará a veces. Cuando esto sucede, la referencia de servicio debe actualizarse.  
  
#### <a name="to-update-a-service-reference"></a>Para actualizar una referencia de servicio  
  
-   En **el Explorador de soluciones**, haga clic en la referencia de servicio y, a continuación, haga clic en **Actualizar referencia de servicio**.  
  
     Se muestra un cuadro de diálogo de progreso mientras se actualiza la referencia de su ubicación original, y el cliente del servicio se vuelve a generar para reflejar los cambios en los metadatos.  
  
## <a name="removing-a-service-reference"></a>Quitar una referencia de servicio  
 Si ya no se utiliza una referencia de servicio, puede quitarlo de la solución.  
  
#### <a name="to-remove-a-service-reference"></a>Para quitar una referencia de servicio  
  
-   En **el Explorador de soluciones**, haga clic en la referencia de servicio y, a continuación, haga clic en **eliminar**.  
  
     El cliente del servicio se quitará de la solución y los metadatos que describen el servicio se quitará el archivo app.config.  
  
    > [!NOTE]
    >  Cualquier código que hace referencia a la referencia de servicio tendrá que quitarse manualmente.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

