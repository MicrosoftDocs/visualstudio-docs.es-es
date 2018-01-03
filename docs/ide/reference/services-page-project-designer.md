---
title: "Página Servicios, Diseñador de proyectos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3a44dc8304274bf0633e891690f6b34d2637dfa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="services-page-project-designer"></a>Página Servicios, Diseñador de proyectos
Los servicios de aplicación cliente proporcionan acceso simplificado al inicio de sesión, los roles y los servicios de perfiles de [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] desde aplicaciones de Windows Forms y Windows Presentation Foundation (WPF). Puede usar la página **Servicios** del **Diseñador de proyectos** para habilitar y configurar servicios de aplicación cliente para el proyecto.  
  
 Con los servicios de aplicación cliente, puede usar un servidor centralizado para autenticar a los usuarios, determinar los roles asignados a cada usuario y almacenar ajustes de aplicación por usuario para compartirlos a través de la red. Para más información, vea [Servicios de aplicación cliente](/dotnet/framework/common-client-technologies/client-application-services).  
  
 Para acceder a la página **Servicios**, seleccione un nodo de proyecto en el **Explorador de soluciones** y luego haga clic en **Propiedades** en el menú **Proyecto**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Servicios**.  
  
> [!NOTE]
>  Los servicios de aplicaciones cliente requieren la versión completa de .NET Framework y no son compatibles con .NET Framework Client Profile. Si la casilla **Habilitar servicios de aplicación cliente** está desactivada, compruebe que **Marco de trabajo de destino** esté establecido en .NET Framework 3.5 o posterior. Para ver el valor de **Marco de trabajo de destino** en C#, abra el Diseñador de proyectos y haga clic en la página **Aplicación**. Para ver el valor de **Marco de trabajo de destino** en Visual Basic, abra el Diseñador de proyectos, haga clic en la página **Compilar** y luego en **Opciones de compilación avanzadas**.  
  
## <a name="task-list"></a>Lista de tareas  
 [Cómo: Configurar servicios de aplicaciones cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Configuración**  
 Este control no se puede modificar en esta página. Para obtener una descripción de este control, vea [Página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Compilar (Página, Diseñador de proyectos) (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plataforma**  
 Este control no se puede modificar en esta página. Para obtener una descripción de este control, vea [Página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Compilar (Página, Diseñador de proyectos) (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Habilitar servicios de aplicación cliente**  
 Seleccione este valor para habilitar los servicios de aplicación cliente. Para usar los servicios de aplicación cliente tiene que especificar las ubicaciones del servicio en la página **Servicios**.  
  
 **Usar autenticación de Windows**  
 Indica que el proveedor de autenticación va a usar la autenticación basada en Windows, es decir, la identidad proporcionada por el sistema operativo Windows.  
  
 **Usar autenticación de formularios**  
 Indica que el proveedor de autenticación va a usar la autenticación de formularios. Esto significa que la aplicación debe proporcionar una interfaz de usuario para el inicio de sesión. Para más información, vea [Cómo: Implementar el inicio de sesión de usuarios con servicios de aplicaciones cliente](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services).  
  
 **Ubicación del servicio de autenticación**  
 Se usa únicamente con la autenticación de formularios. Especifica la ubicación del servicio de autenticación.  
  
 **Opcional: proveedor de credenciales**  
 Se usa únicamente con la autenticación de formularios. Indica la implementación <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> que el servicio de autenticación usará para mostrar un cuadro de diálogo de inicio de sesión cuando su aplicación llame al método `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> y pase cadenas vacías o `null` a los parámetros. Si deja este cuadro en blanco, debe pasar un nombre de usuario válido y una contraseña al método <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>. Tiene que especificar el proveedor de credenciales como un nombre de tipo calificado con el ensamblado. Para obtener más información, consulte <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> y [Nombres del ensamblado](/dotnet/framework/app-domains/assembly-names). En su forma más simple, un nombre de tipo calificado con el ensamblado es similar al ejemplo siguiente: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Ubicación del servicio de roles**  
 Especifica la ubicación del servicio de roles.  
  
 **Ubicación del servicio de configuración web**  
 Especifica la ubicación del servicio de perfil (configuración web).  
  
 **Avanzadas**  
 Abre [Configuración avanzada de servicios (Cuadro de diálogo)](../../ide/reference/advanced-settings-for-services-dialog-box.md), que se puede usar para invalidar el comportamiento predeterminado. Por ejemplo, puede usar este cuadro de diálogo para especificar una base de datos para el almacenamiento sin conexión en lugar de emplear el sistema de archivos local. Para más información, vea [Configuración avanzada de servicios (Cuadro de diálogo)](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## <a name="see-also"></a>Vea también  
 [Servicios de aplicación cliente](/dotnet/framework/common-client-technologies/client-application-services)   
 [Configuración avanzada de servicios (Cuadro de diálogo)](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Cómo: Configurar servicios de aplicaciones cliente](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)   
 [Página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Página Compilar (Diseñador de proyectos) (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
