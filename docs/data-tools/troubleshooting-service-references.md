---
title: Solucionar problemas de referencias de servicio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b57547aa9a5fa3c036a534c85cb55bb1749a421b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-references"></a>Solucionar problemas de referencias de servicio
En este tema se enumera los problemas comunes que pueden producirse cuando se trabaja con [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] o [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] hace referencia en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="error-returning-data-from-a-service"></a>Error al devolver los datos de un servicio  
 Al devolver un `DataSet` o `DataTable` de un servicio, es posible que reciba una excepción "se superó la cuota de tamaño máximo para los mensajes entrantes". De forma predeterminada, la `MaxReceivedMessageSize` propiedad algunos enlaces está configurada en un valor relativamente pequeño para limitar la exposición a ataques por denegación de servicio. Puede aumentar este valor para evitar la excepción. Para obtener más información, consulta <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.  
  
 Para corregir este error:  
  
1.  En **el Explorador de soluciones**, haga doble clic en el archivo app.config para abrirlo.  
  
2.  Busque la `MaxReceivedMessageSize` propiedad y cambie a un valor mayor.  
  
## <a name="cannot-find-a-service-in-my-solution"></a>No se puede encontrar un servicio en mi solución  
 Al hacer clic en el **Discover** botón en el **agregar referencias de servicio** cuadro de diálogo, uno o más proyectos de biblioteca de servicios WCF en la solución no aparecen en la lista de servicios. Esto puede ocurrir si una biblioteca de servicios se ha agregado a la solución, pero aún no se ha compilado.  
  
 Para corregir este error:  
  
-   En **el Explorador de soluciones**, haga clic en el proyecto de biblioteca de servicios WCF y haga clic en **generar**.  
  
## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Error al acceder a un servicio sobre un escritorio remoto  
 Cuando un usuario tiene acceso a un servicio WCF hospedado en Web a través de una conexión a escritorio remota y el usuario no tiene permisos administrativos, se utiliza la autenticación NTLM. Si el usuario no tiene permisos administrativos, el usuario puede recibir el siguiente mensaje de error: "la solicitud HTTP no está autorizada con el esquema de autenticación de cliente 'Anonymous'. El encabezado de autenticación recibido del servidor era 'NTLM'."  
  
 Para corregir este error:  
  
1.  En el proyecto de sitio Web, abra el **propiedades** páginas.  
  
2.  En el **opciones de inicio** ficha, desactive la **la autenticación NTLM** casilla de verificación.  
  
    > [!NOTE]
    >  Debe desactivar la autenticación NTLM sólo para sitios Web que contienen servicios WCF exclusivamente. Seguridad de los servicios WCF se administra a través de la configuración en el archivo web.config. Esto hace que la autenticación NTLM sea innecesaria.  
  
## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Nivel de acceso de las clases generadas configuración no tiene ningún efecto  
 Establecer el **acceso a nivel de las clases generadas** opción en el **configurar referencia de servicio** cuadro de diálogo para **interno** o **Friend** no siempre funciona. Aunque parezca que la opción que se establecerán en el cuadro de diálogo, las clases de soporte resultantes se generará con un nivel de acceso de `Public`.  
  
 Se trata de una limitación conocida de determinados tipos, como los serializados mediante el <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="error-debugging-service-code"></a>Código de servicio de depuración de error  
 Paso a paso por el código para un servicio WCF desde código de cliente, recibirá un error relacionado con símbolos que faltan. Esto puede ocurrir cuando un servicio que formaba parte de la solución se ha movido o eliminado de la solución.  
  
 Primera vez que agrega una referencia a un servicio WCF que forma parte de la solución actual, se agrega una dependencia de compilación explícita entre el proyecto de servicio y el proyecto de cliente de servicio. Esto garantiza que el cliente tiene siempre acceso binarios del servicio actualizada, que es especialmente importante para depurar escenarios como la ejecución paso a paso del código de cliente en el código del servicio.  
  
 Si el proyecto de servicio se quita de la solución, se invalida esta dependencia de compilación explícita. Visual Studio no puede garantizar que se vuelven a generar el proyecto de servicio según sea necesario.  
  
 Para corregir este error, deberá volver a generar manualmente el proyecto de servicio:  
  
1.  En el menú **Herramientas** , haga clic en **Opciones**.  
  
2.  En el **opciones** cuadro de diálogo, expanda **proyectos y soluciones**y, a continuación, seleccione **General**.  
  
3.  Asegúrese de que el **configuraciones de compilación de mostrar avanzadas** casilla de verificación está seleccionada y, a continuación, haga clic en **Aceptar**.  
  
4.  Cargar el proyecto de servicio WCF.  
  
5.  En el **Configuration Manager** cuadro de diálogo, establezca la **configuración de soluciones activas** a **depurar**. Para obtener más información, consulte [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).  
  
6.  En **el Explorador de soluciones**, seleccione el proyecto de servicio WCF.  
  
7.  En el **generar** menú, haga clic en **volver a generar** para recompilar el proyecto de servicio WCF.  
  
## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Servicios de datos WCF no se muestran en el explorador  
 Cuando intenta ver una representación XML de los datos en un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer puede interpretar los datos como una fuente RSS. Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada.  
  
 Para corregir este error, deshabilite las fuentes RSS:  
  
1.  En Internet Explorer, en el **herramientas** menú, haga clic en **opciones de Internet**.  
  
2.  En el **contenido** ficha la **fuentes** sección, haga clic en **configuración**.  
  
3.  En el **configuración de fuente** cuadro de diálogo, desactive la **activar la vista de lectura de fuentes** casilla de verificación y, a continuación, haga clic en **Aceptar**.  
  
4.  Haga clic en **Aceptar** para cerrar el **opciones de Internet** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)