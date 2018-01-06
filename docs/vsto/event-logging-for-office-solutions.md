---
title: Registro de eventos para soluciones de Office | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 55864eda9d62be5988d1d3ab7262c4d34c0662f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="event-logging-for-office-solutions"></a>Registro de eventos para soluciones de Office
  Puede usar el visor de eventos en Windows para ver todos los mensajes de excepción capturados por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , cuando instale o desinstale soluciones de Office. Puede usar estos mensajes desde el registrador de eventos para resolver los problemas de instalación e implementación.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="reading-the-event-log"></a>Leer el registro de eventos  
 Abra el **Visor de eventos** y aplique un filtro para los eventos que desea ver.  
  
#### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Leer el registro de eventos en Windows Server 2003 y Windows XP  
  
1.  En el Panel de control, abra **Herramientas administrativas**.  
  
2.  Abra el **Visor de eventos**.  
  
3.  En la lista de registros de eventos, seleccione **Aplicación**.  
  
4.  En el menú **Ver** , haga clic en **Filtro**.  
  
5.  En la lista **Origen del evento** , seleccione **VSTO 4.0**.  
  
6.  Para los eventos de instalación, escriba **4096** en el cuadro **Identificador del evento**.  
  
7.  Haga clic en **Aceptar** para ver la vista filtrada.  
  
#### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Leer el registro de eventos en Windows 7, Windows Vista y Windows Server 2008  
  
1.  En el Panel de control, abra **Herramientas administrativas**.  
  
2.  Abra el **Visor de eventos**.  
  
3.  Expanda **Registros de Windows**.  
  
4.  En la lista de registros de eventos, seleccione **Aplicación**.  
  
5.  En el menú **Acción** , haga clic en **Filtrar registro actual**.  
  
6.  En la lista **Origen del evento** , seleccione **VSTO 4.0**.  
  
7.  Para los eventos de instalación, escriba **4096** en el cuadro **Identificador del evento**.  
  
8.  Haga clic en **Aceptar** para ver la vista filtrada.  
  
 El visor de eventos incluye la siguiente información:  
  
-   La ubicación del manifiesto de implementación de la solución  
  
-   Un mensaje que describe la causa del error o de la excepción.  
  
 Estos mensajes de excepción pueden ayudarle a determinar el motivo de un problema de instalación, como certificados o ubicaciones de documentos que no son de confianza, o manifiestos de implementación no válidos.  
  
 Una vez desinstalada la solución de Office, los mensajes de excepción permanecen en el registro de eventos.  
  
 Para mostrar o registrar los mensajes de excepción cuando se ejecuta una solución de Office, consulte [depurar proyectos de Office](../vsto/debugging-office-projects.md) y [depurar proyectos de Office](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Localización  
 El lenguaje del mensaje de excepción se determina según el idioma de Visual Studio Tools para Office Runtime. Por ejemplo, si el equipo del usuario final tiene instalado el paquete de idioma japonés, el mensaje de excepción se escribe en japonés en el registro de eventos.  
  
## <a name="disabling-the-event-logger"></a>Deshabilitar el registrador de eventos  
 De forma predeterminada, el registrador de eventos está habilitado cuando se instalan o desinstalan las soluciones de Office. Puede deshabilitar el registrador de eventos estableciendo la variable de entorno VSTO_EVENTLOGDISABLED en "1" (uno).  
  
#### <a name="to-disable-the-event-log"></a>Deshabilitar el registro de eventos  
  
1.  En el Panel de Control, abra **Sistema**.  
  
2.  En la ficha **Opciones avanzadas** , haga clic en **Variables de entorno**.  
  
3.  En el panel **Variables del sistema** , haga clic en **Nueva**.  
  
4.  En el cuadro de diálogo **Nueva variable del sistema** , escriba **VSTO_EVENTLOGDISABLED** en el cuadro **Nombre de la variable** .  
  
5.  En el cuadro **Valor de la variable** , escriba **1**.  
  
6.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Solución de problemas de implementación de las soluciones de Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  