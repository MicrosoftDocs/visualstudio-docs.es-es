---
title: Solucionar problemas de referencias de servicio
description: Revise los problemas comunes que pueden producirse al trabajar con referencias de Windows Communication Foundation (WCF) o Servicios de datos de WCF en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 909291e3f9762593a58df93a9ccc7fe2e82b7952
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866364"
---
# <a name="troubleshoot-service-references"></a>Solucionar problemas de referencias de servicio

En este tema se enumeran los problemas comunes que pueden producirse cuando se trabaja con referencias de Windows Communication Foundation (WCF) o Servicios de datos de WCF en Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Error al devolver datos de un servicio

Cuando se devuelve un `DataSet` o `DataTable` desde un servicio de, es posible que reciba una excepción "se superó la cuota de tamaño máximo para los mensajes entrantes". De forma predeterminada, la `MaxReceivedMessageSize` propiedad de algunos enlaces está establecida en un valor relativamente pequeño para limitar la exposición a los ataques por denegación de servicio. Puede aumentar este valor para evitar la excepción. Para obtener más información, vea <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Para corregir este error:

1. En **Explorador de soluciones**, haga doble clic en el archivo *app.config* para abrirlo.

2. Busque la `MaxReceivedMessageSize` propiedad y cámbiela por un valor mayor.

## <a name="cannot-find-a-service-in-my-solution"></a>No se encuentra un servicio en la solución

Al hacer clic en el botón **detectar** del cuadro de diálogo **Agregar referencias de servicio** , uno o varios proyectos de la biblioteca de servicios WCF de la solución no aparecen en la lista de servicios. Esto puede ocurrir si se ha agregado una biblioteca de servicio a la solución, pero aún no se ha compilado.

Para corregir este error:

- En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto Biblioteca de servicio WCF y haga clic en **compilar**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Error al acceder a un servicio a través de un escritorio remoto

Cuando un usuario tiene acceso a un servicio WCF hospedado en Web a través de una conexión a escritorio remoto y el usuario no tiene permisos administrativos, se usa la autenticación NTLM. Si el usuario no tiene permisos administrativos, el usuario puede recibir el mensaje de error siguiente: "la solicitud HTTP no está autorizada con el esquema de autenticación de cliente ' Anonymous '. El encabezado de autenticación recibido del servidor era ' NTLM '.

Para corregir este error:

1. En el proyecto de sitio web, abra las páginas de **propiedades** .

2. En la pestaña **Opciones de inicio** , desactive la casilla **autenticación NTLM** .

    > [!NOTE]
    > Debe desactivar la autenticación NTLM solo para sitios web que contengan exclusivamente servicios WCF. La seguridad de los servicios WCF se administra a través de la configuración del archivo de *web.config* . Esto hace que la autenticación NTLM sea innecesaria.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>El nivel de acceso de la configuración de las clases generadas no tiene ningún efecto

Si establece la opción **nivel de acceso para clases generadas** en el cuadro de diálogo **Configurar referencias de servicio** en **interno** o **amigo** , es posible que no siempre funcione. Aunque la opción parece estar establecida en el cuadro de diálogo, las clases de compatibilidad resultantes se generan con un nivel de acceso de `Public` .

Se trata de una limitación conocida de ciertos tipos, como los serializados mediante <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>Error de depuración de código de servicio

Al entrar en el código de un servicio WCF desde el código de cliente, es posible que reciba un error relacionado con los símbolos que faltan. Esto puede ocurrir cuando un servicio que formaba parte de la solución se ha migrado o quitado de la solución.

Cuando se agrega por primera vez una referencia a un servicio WCF que forma parte de la solución actual, se agrega una dependencia de compilación explícita entre el proyecto de servicio y el proyecto de cliente de servicio. Esto garantiza que el cliente siempre tenga acceso a los archivos binarios de servicio actualizados, lo que es especialmente importante para los escenarios de depuración, como la ejecución paso a paso del código de cliente en el código del servicio.

Si el proyecto de servicio se quita de la solución, se invalida esta dependencia de compilación explícita. Visual Studio ya no puede garantizar que el proyecto de servicio se vuelva a generar según sea necesario.

Para corregir este error, tiene que volver a generar manualmente el proyecto de servicio:

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. En el cuadro de diálogo **Opciones** , expanda **proyectos y soluciones** y, a continuación, seleccione **General**.

3. Asegúrese de que la casilla **Mostrar configuraciones de compilación avanzadas** está activada y, a continuación, haga clic en **Aceptar**.

4. Cargue el proyecto de servicio WCF.

5. En el cuadro de diálogo **Configuration Manager** , establezca la **configuración de soluciones activa** en **depurar**. Para obtener más información, vea [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).

6. En **Explorador de soluciones**, seleccione el proyecto de servicio WCF.

7. En el menú **compilar** , haga clic en **recompilar** para recompilar el proyecto de servicio WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Servicios de datos de WCF no se muestran en el explorador

Cuando intenta ver una representación XML de los datos en un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , Internet Explorer puede interpretar los datos como una fuente RSS. Asegúrese de que la opción para mostrar fuentes RSS está deshabilitada.

Para corregir este error, deshabilite las fuentes RSS:

1. En Internet Explorer, en el menú **Herramientas**, haga clic en **Opciones de Internet**.

2. En la pestaña **contenido** , en la sección **fuentes** , haga clic en **configuración**.

3. En el cuadro de diálogo **configuración de fuente** , desactive la casilla **activar la vista de lectura de fuentes** y, a continuación, haga clic en **Aceptar**.

4. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones de Internet** .

## <a name="see-also"></a>Vea también

- [Servicios de Windows Communication Foundation y servicios de datos WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
