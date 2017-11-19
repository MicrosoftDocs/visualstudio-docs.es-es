---
title: Seguridad para las soluciones de SharePoint | Documentos de Microsoft
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
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c57626827be8487d19cd546bc31bd32b0859cec7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="security-for-sharepoint-solutions"></a>Seguridad para las soluciones de SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]incorpora las siguientes características para ayudar a mejorar la seguridad de las aplicaciones de SharePoint.  
  
## <a name="safe-control-entries"></a>Entradas de controles seguros  
 Cada elemento de proyecto de SharePoint creado en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene un **entradas de controles seguros** colección de controles de la propiedad que representa una caja fuerte. Su **seguro** subpropiedad le permite especificar los controles que se consideran seguros. Para obtener más información, consulte [proporcionando información empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) y [Specifying Safe Web Parts](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers, atributo  
 De forma predeterminada, solo las aplicaciones que son de plena confianza por el sistema de seguridad (CAS) de acceso del código de tiempo de ejecución pueden tener acceso a un ensamblado de código administrado compartido. Marcar un ensamblado de plena confianza con el atributo AllowPartiallyTrustedCallers permite a los ensamblados de confianza parcial tener acceso a él.  
  
 El atributo AllowPartiallyTrustedCallers se agrega a cualquier solución de SharePoint que no se implementó en la caché global de ensamblados del sistema ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Esto incluye soluciones en espacio aislado o las soluciones implementadas en el directorio Bin de la aplicación de SharePoint. Para obtener más información, consulte [cambios de seguridad de versión 1 de Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177515) y [implementar elementos Web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## <a name="safe-against-script-property"></a>Seguridad de Script (propiedad)  
 *Inyección de script* es la inserción de código potencialmente malintencionado en controles o las páginas Web. Para ayudar a proteger los sitios de SharePoint 2010 contra la inyección de script, colaboradores no pueden ver o editar elementos Web o a sus propiedades de forma predeterminada. Este comportamiento se controla mediante un atributo de SafeControl denominado SafeAgainstScript. En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], establezca este atributo en un elemento de proyecto **entradas de controles seguros** subpropiedad **Safe Against Script**. Para obtener más información, consulte [proporcionando información empaquetado e implementación de elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) y [Cómo: marcar los controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista y Windows 7 User Account Control  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporan una característica de seguridad que se conoce como Control de cuentas de usuario (UAC). Para poder desarrollar soluciones de SharePoint mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sistemas [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], UAC requiere que se ejecute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como administrador del sistema. Desde el **iniciar** menú, abra el menú contextual para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]y, a continuación, elija **ejecutar como administrador**.  
  
 Para configurar el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] acceso directo a siempre ejecutar como administrador, abra el menú contextual, elija **propiedades**, elija la **avanzadas** botón en la **propiedades**cuadro de diálogo y, a continuación, seleccione la **ejecutar como administrador** casilla de verificación.  
  
 Para obtener más información, consulte [descripción y configuración de Control de cuentas de usuario en Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). y [Control de cuentas de usuario de Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## <a name="sharepoint-permissions-considerations"></a>Consideraciones sobre los permisos de SharePoint  
 Para desarrollar las soluciones de SharePoint, debe tener los permisos necesarios para ejecutar y depurar soluciones de SharePoint. Antes de probar una solución de SharePoint, dé los pasos siguientes para asegurarse de que tiene los permisos necesarios:  
  
1.  Agregue su cuenta de usuario como administrador del sistema.  
  
2.  Agregue su cuenta de usuario como administrador del conjunto de servidores en el servidor de SharePoint.  
  
    1.  En Administración Central de SharePoint 2010, elija la **administrar el grupo de administradores de la granja de servidores** vínculo.  
  
    2.  En el **administradores de la granja** página, elija la **New** opción de menú  
  
3.  Agregue su cuenta de usuario al grupo WSS_ADMIN_WPG.  
  
## <a name="additional-security-resources"></a>Recursos de seguridad adicionales  
 Para obtener más información acerca de los problemas de seguridad, vea lo siguiente.  
  
### <a name="visual-studio-security"></a>Seguridad de Visual Studio  
  
-   [Seguridad y permisos de usuario](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Seguridad en nativo y código de .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Seguridad en .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>Seguridad de SharePoint  
  
-   [Seguridad y administración de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Centro de recursos de seguridad de SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Proteger los elementos Web de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Seguridad mejorada de la aplicación Web: Amenazas y contramedidas](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>Seguridad general  
  
-   [Ciclo de vida de desarrollo de seguridad MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Creación de aplicaciones ASP.NET seguras: Autenticación, autorización y comunicación segura](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  