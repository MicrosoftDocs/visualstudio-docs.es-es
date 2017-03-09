---
title: "Configuraci&#243;n avanzada de servicios (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedServices"
helpviewer_keywords: 
  - "Cuadro de diálogo Configuración avanzada de servicios"
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuraci&#243;n avanzada de servicios (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los servicios de aplicaciones cliente proporcionan acceso simplificado al inicio de sesión, los roles y los servicios de perfil de [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] procedentes de aplicaciones de Windows Forms y Windows Presentation Foundation \(WPF\).  Puede utilizar la página **Servicios** del **Diseñador de proyectos** para configurar servicios de aplicación cliente.  Para obtener más información acerca de la página **Servicios**, vea [Página Servicios, Diseñador de proyectos](../../ide/reference/services-page-project-designer.md).  
  
 Utilice el cuadro de diálogo **Configuración avanzada de servicios** de la página **Servicios** en el **Diseñador de proyectos** a fin de establecer una configuración avanzada para los servicios de aplicación cliente.  Mediante estos valores de configuración, puede invalidar algunos comportamientos predeterminados del servicio de aplicación para habilitar escenarios menos comunes.  Para obtener más información, vea [Servicios de aplicación cliente](../Topic/Client%20Application%20Services.md).  
  
 Para obtener acceso al cuadro de diálogo **Configuración avanzada de servicios**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, a continuación, haga clic en **Propiedades** en el menú **Proyecto**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Servicios** y, a continuación, en el botón **Avanzadas**.  Este botón estará deshabilitado hasta que se habiliten los servicios de aplicación cliente.  
  
## Lista de tareas  
 [Cómo: Configurar servicios de aplicaciones cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)  
  
 [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/es-es/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## Lista de UIElement  
 **Guardar hash de contraseña para permitir el inicio de sesión sin conexión**  
 Especifica si se va a almacenar en la caché local una forma cifrada de la contraseña del usuario para permitir a éste iniciar sesión cuando la aplicación está en modo sin conexión.  Para obtener más información, vea [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/es-es/f792cb16-8520-4a0f-9dc9-07bfbc454e38).  Esta opción está seleccionada de forma predeterminada.  
  
 **Exigir que los usuarios vuelvan a iniciar sesión cuando expire la cookie del servidor**  
 Especifica si los usuarios autenticados anteriormente se vuelven a autenticar automáticamente cuando la aplicación tiene acceso a los roles o al servicio de perfil y la cookie de autenticación del servidor ha expirado.  Seleccione esta opción para denegar el acceso a los servicios de la aplicación y requerir una reautenticación explícita después de que la cookie expire.  Esta opción resulta útil para las aplicaciones implementadas en ubicaciones públicas a fin de asegurarse de que los usuarios que dejan la aplicación en ejecución después de usarla no permanezcan autenticados indefinidamente.  Esta opción está desactivada de forma predeterminada.  
  
 **Tiempo de espera de la caché del servicio de roles**  
 Especifica el tiempo durante el que el proveedor de roles de cliente utilizará valores de rol almacenados en caché en lugar de obtener acceso al servicio de roles.  Establezca este intervalo de tiempo en un valor pequeño si los roles se actualizan con frecuencia o a un valor mayor si los roles se actualizan con poca frecuencia.  El valor predeterminado es un día.  
  
 El proveedor de roles obtiene acceso a los valores de rol almacenados en caché o el servicio de roles al llamar al método <xref:System.Web.Security.RolePrincipal.IsInRole%2A>.  Para borrar la caché mediante programación y hacer que este método tenga acceso al servicio remoto, llame al método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Usar cadena de conexión personalizada**  
 Especifica si los proveedores de servicios del cliente utilizarán un almacén de datos personalizado para la caché local.  De forma predeterminada, los proveedores de servicios utilizarán el sistema de archivos local para la caché.  Al seleccionar esta opción, el cuadro de texto se rellenará automáticamente con una cadena de conexión predeterminada.  Puede mantener la cadena de conexión predeterminada para generar y utilizar automáticamente una base de datos de SQL Server Compact Edition o bien especificar una cadena de conexión a una base de datos de SQL Server existente.  Para obtener más información, vea [Cómo: Configurar servicios de aplicaciones cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md).  Esta opción está desactivada de forma predeterminada.  
  
## Vea también  
 [Servicios de aplicación cliente](../Topic/Client%20Application%20Services.md)   
 [Página Servicios, Diseñador de proyectos](../../ide/reference/services-page-project-designer.md)   
 [Cómo: Configurar servicios de aplicaciones cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)   
 [How to: Work Offline with Client Application Services](http://msdn.microsoft.com/es-es/f792cb16-8520-4a0f-9dc9-07bfbc454e38)