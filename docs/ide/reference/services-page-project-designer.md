---
title: "P&#225;gina Servicios, Dise&#241;ador de proyectos | Microsoft Docs"
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
  - "vb.ProjectPropertiesServices"
helpviewer_keywords: 
  - "Página Servicios del Diseñador de proyectos"
  - "Diseñador de proyectos, página Servicios"
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina Servicios, Dise&#241;ador de proyectos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los servicios de aplicaciones cliente proporcionan acceso simplificado al inicio de sesión, los roles y los servicios de perfil de [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] procedentes de aplicaciones de Windows Forms y Windows Presentation Foundation \(WPF\).  Puede utilizar la página **Servicios** del **Diseñador de proyectos** para habilitar y configurar los servicios de aplicación cliente para su proyecto.  
  
 Con los servicios de aplicación cliente, se puede utilizar un servidor centralizado para autenticar a los usuarios, determinar los roles asignados a cada usuario y almacenar la configuración de aplicaciones por usuario que se puede compartir en la red.  Para obtener más información, vea [Servicios de aplicación cliente](../Topic/Client%20Application%20Services.md).  
  
 Para obtener acceso a la página **Servicios**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, a continuación, haga clic en **Propiedades** en el menú **Proyecto**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Servicios**.  
  
> [!NOTE]
>  Los servicios de aplicaciones cliente necesitan la versión completa de .NET Framework y no se admiten en .NET Framework Client Profile.  Si la casilla **Habilitar servicios de aplicación cliente** está desactivada, compruebe que **Versión de .NET Framework de destino** esté establecido en .NET Framework 3.5 o posterior.  Para ver el valor de **Versión de .NET Framework de destino** en C\#, abra el Diseñador de proyectos y, a continuación, haga clic en la página **Aplicación**.  Para ver el valor de **Versión de .NET Framework de destino** en Visual Basic, abra el Diseñador de proyectos, haga clic en la página **Compilar** y, a continuación, haga clic en **Opciones de compilación avanzadas**.  
  
## Lista de tareas  
 [Cómo: Configurar servicios de aplicaciones cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)  
  
## Lista de UIElement  
 **Configuración**  
 Este control no se puede modificar en esta página.  Para obtener una descripción de este control, vea [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plataforma**  
 Este control no se puede modificar en esta página.  Para obtener una descripción de este control, vea [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md) o [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Habilitar servicios de aplicación cliente**  
 Seleccione esta opción para habilitar los servicios de aplicación cliente.  Para utilizar los servicios de aplicación cliente , debe especificar las ubicaciones de los servicios en la página **Servicios**.  
  
 **Utilizar autenticación de Windows**  
 Indica que el proveedor de autenticación utilizará la autenticación basada en Windows, es decir, la identidad proporcionada por el sistema operativo Windows.  
  
 **Usar autenticación de formularios**  
 Indica que el proveedor de autenticación utilizará la autenticación de formularios.  Esto significa que la aplicación debe proporcionar una interfaz de usuario para el inicio de sesión.  Para obtener más información, vea [Cómo: Implementar el inicio de sesión de usuarios con servicios de aplicaciones cliente](../Topic/How%20to:%20Implement%20User%20Login%20with%20Client%20Application%20Services.md).  
  
 **Ubicación del servicio de autenticación**  
 Sólo se utiliza con la autenticación de formularios.  Especifica la ubicación del servicio de autenticación.  
  
 **Opcional: proveedor de credenciales**  
 Sólo se utiliza con la autenticación de formularios.  Indica la implementación de <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> que utilizará el servicio de autenticación para mostrar un cuadro de diálogo de inicio de sesión cuando la aplicación llama al método `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> y pasa cadenas vacías o `null` para los parámetros.  Si deja este cuadro en blanco, debe pasar un nombre de usuario y una contraseña válidos al método <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>.  Debe especificar el proveedor de credenciales como un nombre de tipo calificado con el nombre de ensamblado.  Para obtener más información, vea <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> y [Nombres de ensamblado](../Topic/Assembly%20Names.md).  En su forma más simple, un nombre de tipo calificado con el nombre de ensamblado es similar al ejemplo siguiente: `MyNamespace.MyLoginClass, MyAssembly`  
  
 **Ubicación del servicio de roles**  
 Especifica la ubicación del servicio de roles.  
  
 **Ubicación del servicio de configuración web**  
 Especifica la ubicación del servicio de perfil \(configuración web\).  
  
 **Avanzado**  
 Abre [Configuración avanzada de servicios \(Cuadro de diálogo\)](../../ide/reference/advanced-settings-for-services-dialog-box.md), que puede utilizar para invalidar el comportamiento predeterminado.  Por ejemplo, puede utilizar este cuadro de diálogo para especificar una base de datos para el almacenamiento sin conexión en lugar de utilizar el sistema de archivos local.  Para obtener más información, vea [Configuración avanzada de servicios \(Cuadro de diálogo\)](../../ide/reference/advanced-settings-for-services-dialog-box.md).  
  
## Vea también  
 [Servicios de aplicación cliente](../Topic/Client%20Application%20Services.md)   
 [Configuración avanzada de servicios \(Cuadro de diálogo\)](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [Cómo: Configurar servicios de aplicaciones cliente](../Topic/How%20to:%20Configure%20Client%20Application%20Services.md)   
 [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md)   
 [Introduction to the Project Designer](http://msdn.microsoft.com/es-es/898dd854-c98d-430c-ba1b-a913ce3c73d7)