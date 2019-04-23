---
title: Solucionar problemas de referencias de servicio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cff1677ab9209ce2a51b7587c410731a71e27eb0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056724"
---
# <a name="troubleshooting-service-references"></a>Solucionar problemas de referencias de servicio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
En este tema se enumera los problemas comunes que pueden producirse cuando se trabaja con [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] o [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] hace referencia en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="error-returning-data-from-a-service"></a>Error al devolver datos de un servicio
 Cuando vuelva un `DataSet` o `DataTable` desde un servicio, puede recibir una excepción "se superó la cuota de tamaño máximo para los mensajes entrantes". De forma predeterminada, el `MaxReceivedMessageSize` algunos enlaces de propiedad se establece en un valor relativamente pequeño para limitar la exposición a ataques por denegación de servicio. Puede aumentar este valor para evitar la excepción.

 Para corregir este error:

1. En **el Explorador de soluciones**, haga doble clic en el archivo app.config para abrirlo.

2. Busque el `MaxReceivedMessageSize` propiedad y cámbielo a un valor mayor.

## <a name="cannot-find-a-service-in-my-solution"></a>No se puede encontrar un servicio en mi solución
 Al hacer clic en el **Discover** situado en la **agregar referencias de servicio** cuadro de diálogo, uno o varios proyectos de biblioteca de servicios WCF en la solución no aparecen en la lista de servicios. Esto puede ocurrir si una biblioteca de servicios se ha agregado a la solución, pero aún no se ha compilado.

 Para corregir este error:

- En **el Explorador de soluciones**, haga clic en el proyecto de biblioteca de servicios WCF y haga clic en **compilar**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Error al acceder a un servicio a través de un escritorio remoto
 Cuando un usuario accede a un servicio WCF hospedado en Web a través de una conexión a escritorio remota y el usuario no tiene permisos administrativos, se usa la autenticación NTLM. Si el usuario no tiene permisos administrativos, el usuario puede recibir el mensaje de error siguiente: "La solicitud HTTP no está autorizada con el esquema de autenticación de cliente 'Anónimo'. El encabezado de autenticación recibido del servidor era 'NTLM'."

 Para corregir este error:

1. En el proyecto de sitio Web, abra el **propiedades** páginas.

2. En el **opciones de inicio** ficha, desactive la **la autenticación NTLM** casilla de verificación.

    > [!NOTE]
    > Debe desactivar la autenticación NTLM sólo para sitios Web que contengan exclusivamente los servicios WCF. Seguridad de los servicios WCF se administra a través de la configuración en el archivo web.config. Esto hace que la autenticación NTLM innecesaria.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Nivel de acceso para clases generadas No tiene efecto
 Establecer el **tener acceso a nivel de las clases generadas** opción el **configurar referencia de servicio** cuadro de diálogo para **interno** o **Friend** no siempre funcionen. Aunque parezca la opción debe establecerse en el cuadro de diálogo, se generará las clases resultantes de soporte técnico con un nivel de acceso de `Public`.

 Se trata de una limitación conocida de determinados tipos, como los serializados mediante el <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Código de servicio de depuración de errores
 Paso a paso en el código para un servicio WCF desde código de cliente, recibirá un error relacionado con los símbolos que faltan. Esto puede ocurrir cuando un servicio que formaba parte de la solución se ha movido o eliminado de la solución.

 Al agregar una referencia a un servicio WCF que forma parte de la solución actual en primer lugar, se agrega una dependencia de compilación explícita entre el proyecto de servicio y el proyecto de cliente del servicio. Esto garantiza que el cliente siempre tiene acceso a archivos binarios del servicio actualizada, que es especialmente importante para depurar escenarios como la ejecución paso a paso del código de cliente en el código del servicio.

 Si el proyecto de servicio se quita de la solución, se invalida esta dependencia de compilación explícita. Visual Studio no puede garantizar que se recompile el proyecto de servicio según sea necesario.

 Para corregir este error, tendrá que volver a crear el proyecto de servicio:

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. En el **opciones** cuadro de diálogo, expanda **proyectos y soluciones**y, a continuación, seleccione **General**.

3. Asegúrese de que el **avanzada de mostrar configuraciones de compilación** casilla de verificación está seleccionada y, a continuación, haga clic en **Aceptar**.

4. Cargue el proyecto de servicio WCF. Para obtener más información, vea [Cómo: Crear soluciones de varios proyectos](http://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).

5. En el **Configuration Manager** cuadro de diálogo, establezca el **configuración de soluciones activas** a **depurar**. Para obtener más información, vea [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).

6. En **el Explorador de soluciones**, seleccione el proyecto de servicio WCF.

7. En el **compilar** menú, haga clic en **recompilar** para recompilar el proyecto de servicio WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Data Services de WCF no se muestran en el explorador
 Cuando intenta ver una representación XML de los datos en un [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], Internet Explorer puede interpretar los datos como una fuente RSS. Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada.

 Para corregir este error, deshabilite las fuentes RSS:

1. En Internet Explorer, en el menú **Herramientas**, haga clic en **Opciones de Internet**.

2. En el **contenido** ficha la **fuentes** sección, haga clic en **configuración**.

3. En el **configuración de fuente** cuadro de diálogo, desactive la **activar la vista de lectura de fuentes** casilla de verificación y, a continuación, haga clic en **Aceptar**.

4. Elija **Aceptar** para cerrar el cuadro de diálogo **Opciones de Internet**.

## <a name="see-also"></a>Vea también

- [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)