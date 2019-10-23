---
title: Configuración avanzada de servicios (Cuadro de diálogo)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed0ce1eecbd9bcc9508f6fc884220a59eb428df0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652783"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Configuración avanzada de servicios (Cuadro de diálogo)
Los servicios de aplicaciones cliente proporcionan acceso simplificado al inicio de sesión, los roles y los servicios de perfiles de [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] desde aplicaciones de Windows Forms y Windows Presentation Foundation (WPF). Puede usar la página **Servicios** del **Diseñador de proyectos** para configurar los servicios de aplicación cliente. Para obtener más información sobre la página **Servicios**, consulte [Página Servicios, Diseñador de proyectos](../../ide/reference/services-page-project-designer.md).

Use el cuadro de diálogo **Configuración avanzada de servicios** de la página **Servicios** en el **Diseñador de proyectos** para configurar opciones avanzadas de servicios de aplicación cliente. Al usar estas opciones, puede invalidar algunos comportamientos de servicio de aplicación predeterminados para habilitar escenarios menos comunes. Para obtener más información, consulte [Servicios de aplicación cliente](/dotnet/framework/common-client-technologies/client-application-services).

Para acceder al cuadro de diálogo **Configuración avanzada de servicios**, seleccione un nodo de proyecto en el **Explorador de soluciones** y luego haga clic en **Propiedades** en el menú **Proyecto**. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Servicios** y después haga clic en el botón **Avanzadas**. Este botón se deshabilitará hasta que habilite los servicios de aplicación cliente.

## <a name="task-list"></a>Lista de tareas

- [Cómo: Configurar servicios de aplicaciones cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>Lista de UIElement

 **Guardar hash de contraseña para permitir el inicio de sesión sin conexión** Especifica si se almacena en caché de forma local una forma cifrada de la contraseña del usuario para permitir que inicie sesión cuando la aplicación está en modo sin conexión. Esta opción está seleccionada de forma predeterminada.

 **Exigir que los usuarios vuelvan a iniciar sesión cuando expire la cookie del servidor** Especifica si los usuarios autenticados previamente se vuelven a autenticar de forma automática cuando la aplicación accede a los roles o al servicio de perfil y la cookie de autenticación de servidor ha expirado. Seleccione esta opción para denegar el acceso a los servicios de aplicación y requerir una reautenticación explícita después de que expire la cookie. Esta opción es útil en aplicaciones implementadas en ubicaciones públicas, ya que garantiza que los usuarios que dejan la aplicación en ejecución después de usarla no permanecen autenticados indefinidamente. Esta opción se encuentra desactivada de forma predeterminada.

 **Tiempo de espera de caché del servicio de roles** Especifica la cantidad de tiempo que el proveedor de roles de cliente usa valores de rol almacenados en caché en lugar de acceder al servicio de roles. Establezca este intervalo de tiempo en un valor pequeño si los roles se actualizan con frecuencia o en un valor mayor si se actualizan con poca frecuencia. El valor predeterminado es un día.

Cuando se llama al método <xref:System.Web.Security.RolePrincipal.IsInRole%2A>, el proveedor de roles accede a los valores de rol almacenados en caché o al servicio de roles. Para borrar la caché y forzar este método para tener acceso al servicio remoto mediante programación, llame al método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.

 **Usar cadena de conexión personalizada** Especifica si los proveedores de servicios de cliente usan un almacén de datos personalizado para la caché local. De manera predeterminada, los proveedores de servicios usarán el sistema de archivos local para la caché. Al seleccionar esta opción se rellenará de forma automática el cuadro de texto con una cadena de conexión predeterminada. Puede hacer que la cadena de conexión predeterminada genere y use de forma automática una base de datos de SQL Server Compact Edition, o puede especificar una cadena de conexión a una base de datos de SQL Server existente. Para obtener más información, vea [Cómo: Configurar servicios de aplicaciones cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services). Esta opción se encuentra desactivada de forma predeterminada.

## <a name="see-also"></a>Vea también

- [Servicios de aplicación cliente](/dotnet/framework/common-client-technologies/client-application-services)
- [Página Servicios, Diseñador de proyectos](../../ide/reference/services-page-project-designer.md)
- [Cómo: Configurar servicios de aplicaciones cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)