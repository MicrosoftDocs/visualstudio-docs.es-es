---
title: Configuración avanzada de servicios (Cuadro de diálogo) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea79a5539ad41a4f6e56a6069889e06bc45dde65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573754"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Configuración avanzada de servicios (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [configuración avanzada para el cuadro de diálogo Servicios](https://docs.microsoft.com/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
  
Los servicios de aplicaciones cliente proporcionan acceso simplificado al inicio de sesión, los roles y los servicios de perfiles de [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] desde aplicaciones de Windows Forms y Windows Presentation Foundation (WPF). Puede usar la página **Servicios** del **Diseñador de proyectos** para configurar los servicios de aplicación cliente. Para obtener más información sobre la página **Servicios**, consulte [Página Servicios, Diseñador de proyectos](../../ide/reference/services-page-project-designer.md).  
  
 Use el cuadro de diálogo **Configuración avanzada de servicios** de la página **Servicios** en el **Diseñador de proyectos** para configurar opciones avanzadas de servicios de aplicación cliente. Al usar estas opciones, puede invalidar algunos comportamientos de servicio de aplicación predeterminados para habilitar escenarios menos comunes. Para obtener más información, consulte [Servicios de aplicación cliente](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Para acceder al cuadro de diálogo **Configuración avanzada de servicios**, seleccione un nodo de proyecto en el **Explorador de soluciones** y luego haga clic en **Propiedades** en el menú **Proyecto**. Cuando aparezca el **Diseñador de proyectos**, haga clic en la pestaña **Servicios** y después haga clic en el botón **Avanzadas**. Este botón se deshabilitará hasta que habilite los servicios de aplicación cliente.  
  
## <a name="task-list"></a>Lista de tareas  
 [Cómo: Configurar servicios de aplicaciones cliente](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [Cómo: Trabajar sin conexión con servicios de aplicaciones cliente](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Guardar hash de contraseña para permitir el inicio de sesión sin conexión**  
 Especifica si se almacenará en caché de forma local una forma cifrada de la contraseña del usuario para permitir que el usuario inicie sesión cuando la aplicación está en modo sin conexión. Para obtener más información, consulte [Cómo: Trabajar sin conexión con servicios de aplicaciones cliente](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Esta opción está seleccionada de forma predeterminada.  
  
 **Exigir que los usuarios vuelvan a iniciar sesión cuando expire la cookie del servidor**  
 Especifica si los usuarios autenticados previamente se vuelven a autenticar de forma automática cuando la aplicación accede a los roles o al servicio de perfil y la cookie de autenticación de servidor ha expirado. Seleccione esta opción para denegar el acceso a los servicios de aplicación y requerir una reautenticación explícita después de que expire la cookie. Esta opción es útil en aplicaciones implementadas en ubicaciones públicas, ya que garantiza que los usuarios que dejan la aplicación en ejecución después de usarla no permanecen autenticados indefinidamente. Esta opción se encuentra desactivada de forma predeterminada.  
  
 **Tiempo de espera de caché del servicio de roles**  
 Especifica la cantidad de tiempo que el proveedor de roles de cliente usará valores de rol almacenados en caché en lugar de acceder al servicio de roles. Establezca este intervalo de tiempo en un valor pequeño si los roles se actualizan con frecuencia o en un valor mayor si se actualizan con poca frecuencia. El valor predeterminado es un día.  
  
 Cuando se llama al método <xref:System.Web.Security.RolePrincipal.IsInRole%2A>, el proveedor de roles accede a los valores de rol almacenados en caché o al servicio de roles. Para borrar la caché y forzar este método para tener acceso al servicio remoto mediante programación, llame al método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Usar cadena de conexión personalizada**  
 Especifica si los proveedores de servicios de cliente usarán un almacén de datos personalizado para la caché local. De manera predeterminada, los proveedores de servicios usarán el sistema de archivos local para la caché. Al seleccionar esta opción se rellenará de forma automática el cuadro de texto con una cadena de conexión predeterminada. Puede hacer que la cadena de conexión predeterminada genere y use de forma automática una base de datos de SQL Server Compact Edition, o puede especificar una cadena de conexión a una base de datos de SQL Server existente. Para obtener más información, consulte [Cómo: Configurar servicios de aplicaciones cliente](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Esta opción se encuentra desactivada de forma predeterminada.  
  
## <a name="see-also"></a>Vea también  
 [Servicios de aplicación cliente](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Página Servicios, Diseñador de proyectos](../../ide/reference/services-page-project-designer.md)   
 [Cómo: Configurar servicios de aplicaciones cliente](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Cómo: Trabajar sin conexión con servicios de aplicaciones cliente](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)



