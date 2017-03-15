---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
En este tema se enumeran los problemas comunes que pueden producirse al trabajar con referencias de [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] o [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Error al devolver datos de un servicio  
 Al devolver `DataSet` o `DataTable` de un servicio, puede recibir una excepción "Se ha superado la cuota de tamaño máximo para los mensajes entrantes".  De forma predeterminada, la propiedad `MaxReceivedMessageSize` para algunos enlaces está establecida en un valor relativamente pequeño para limitar la exposición a los ataques por denegación de servicio.  Puede aumentar este valor para evitar la excepción.  Para obtener más información, vea <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>.  
  
 Para corregir este error:  
  
1.  En el **Explorador de soluciones**, haga doble clic en el archivo app.config para abrirlo.  
  
2.  Busque la propiedad `MaxReceivedMessageSize` y cámbiela a un valor mayor.  
  
## No se puede buscar un servicio en Mi Solución  
 Al hacer clic en el botón **Detectar** del cuadro de diálogo **Agregar referencia de servicio**, uno o más proyectos de biblioteca de servicios de WCF de la solución no aparecen en la lista de servicios.  Esto puede ocurrir si se ha agregado una biblioteca de servicios a la solución pero no se ha compilado aún.  
  
 Para corregir este error:  
  
-   En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto de biblioteca de servicios de WCF y haga clic en **Compilar**.  
  
## Error al tener acceso a un servicio sobre un escritorio remoto  
 Cuando un usuario obtiene acceso a un servicio de WCF hospedado en web a través de una conexión a escritorio remoto, y no tiene permisos administrativos, se usa la autenticación NTLM.  Si el usuario no tiene permisos administrativos, puede que reciba el siguiente mensaje de error: "La solicitud HTTP no está autorizada con el esquema de autenticación de cliente 'Anónimo'.  El encabezado de autenticación recibido del servidor era 'NTLM'."  
  
 Para corregir este error:  
  
1.  En el proyecto de sitio web, abra las páginas **Propiedades**.  
  
2.  En la ficha **Opciones de inicio**, desactive la casilla **Autenticación NTLM**.  
  
    > [!NOTE]
    >  Debería solamente desactivar la autenticación NTLM para los sitios web que contienen servicios WCF exclusivamente.  La seguridad para los servicios WCF se administra a través de la configuración en el archivo web.config.  Esto hace que la autenticación NTLM sea innecesaria.  
  
 Para obtener más información, vea [Solución de problemas de excepciones: System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md).  
  
## La opción Nivel de acceso de las clases generadas no surte ningún efecto  
 Es posible que establecer la opción **Nivel de acceso de las clases generadas** del cuadro de diálogo **Configurar referencia de servicio** en **Interno** o **Friend** no siempre funcione.  Aunque la opción parece que está establecida en el cuadro de diálogo, las clases de soporte resultantes se generarán con un nivel de acceso `Public`.  
  
 Ésta es una limitación conocida de determinados tipos, como los serializados mediante <xref:System.Xml.Serialization.XmlSerializer>.  
  
## Código de servicio de depuración de error  
 Si se encuentra con el código para un servicio WCF a partir de un código de cliente, es posible que vea un error relacionado con símbolos que faltan.  Esto puede ocurrir al mover o quitar un servicio que formaba parte de la solución.  
  
 Al agregar por primera vez una referencia a un servicio WCF que forma parte de la solución actual, se agrega una dependencia de compilación explícita entre el proyecto de servicio y el proyecto de cliente de servicio.  Esto garantiza que el cliente siempre tiene acceso a binarios de servicio actualizados, lo que es especialmente importante para depurar escenarios como cuando se pasa del código de cliente al código de servicio.  
  
 Si se quita el proyecto de servicio de la solución, se invalida esta dependencia de compilación explícita.  Visual Studio ya no puede garantizar que el proyecto de servicio se recompile cuando sea necesario.  
  
 Para corregir este error, tiene que recompilar manualmente el proyecto de servicio:  
  
1.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones** y, a continuación, seleccione **General**.  
  
3.  Asegúrese de que la casilla **Mostrar configuraciones de compilación avanzadas** esté activada y, a continuación, haga clic en **Aceptar**.  
  
4.  Cargue el proyecto de servicio WCF.  Para obtener más información, vea [Cómo: Crear soluciones de varios proyectos](http://msdn.microsoft.com/es-es/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).  
  
5.  En el cuadro de diálogo **Administrador de configuración**, establezca **Configuración de soluciones activas** en **Depurar**.  Para obtener más información, vea [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).  
  
6.  En el **Explorador de soluciones**, seleccione el proyecto de servicio WCF.  
  
7.  En el menú **Compilar**, haga clic en **Recompilar** recompilar el proyecto de servicio WCF.  
  
## Los Servicios de datos de WCF no aparecen en el explorador  
 Al intentar ver una representación XML de los datos en un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer puede interpretar los datos erróneamente como fuente RSS.  Debe asegurarse de que la opción para mostrar las fuentes RSS está deshabilitada.  
  
 Para corregir este error, deshabilite las fuentes RSS:  
  
1.  En Internet Explorer, en el menú **Herramientas**, haga clic en **Opciones de Internet**.  
  
2.  En la ficha **Contenido**, en la sección **Fuentes**, haga clic en **Configuración**.  
  
3.  En el cuadro de diálogo **Configuración de fuente**, desactive la casilla **Activar la vista de lectura de fuentes** y, a continuación, haga clic en **Aceptar**.  
  
4.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones de Internet**.  
  
## Vea también  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/es-es/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)