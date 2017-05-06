---
title: "Seguridad para las soluciones de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "seguridad [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, seguridad"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Seguridad para las soluciones de SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incorpora las siguientes características que ayudan a mejorar la seguridad de las aplicaciones de SharePoint.  
  
## Entradas de controles seguros  
 Todos los elementos de proyecto de SharePoint que se crean en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tienen una propiedad **Safe Control Entries** que representa una colección de controles seguros.  Su subpropiedad **Safe** permite especificar los controles que se consideran seguros.  Para obtener más información, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) y [Especificar los elementos web seguros](http://go.microsoft.com/fwlink/?LinkId=177521).  
  
## AllowPartiallyTrustedCallers \(Atributo\)  
 De forma predeterminada, solo las aplicaciones que son de plena confianza para el sistema de seguridad de acceso del código en tiempo de ejecución pueden tener acceso a un ensamblado del código administrado compartido.  Cuando se marca un ensamblado de plena confianza con el atributo AllowPartiallyTrustedCallers, los ensamblados de confianza parcial pueden obtener acceso a él.  
  
 El atributo AllowPartiallyTrustedCallers se agrega a cualquier solución de SharePoint que no esté implementada en la memoria caché global de ensamblados \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\) del sistema.  Entre ellas, se incluyen las soluciones en espacios aislados o las soluciones implementadas en el directorio Bin de la aplicación de SharePoint.  Para obtener más información, vea [Cambios de seguridad de la versión 1 para Microsoft.NET framework](http://go.microsoft.com/fwlink/?LinkId=177515) y [Elementos de implementación web en la base de SharePoint](http://go.microsoft.com/fwlink/?LinkId=177509).  
  
## Safe Against Script \(Propiedad\)  
 La *inyección de script* es la inserción de código potencialmente malintencionado en controles o páginas web.  Para ayudar a proteger los sitios de SharePoint 2010 contra la inyección de script, de forma predeterminada, los colaboradores no pueden ver o editar elementos web ni sus propiedades.  Este comportamiento se controla mediante un atributo de SafeControl denominado SafeAgainstScript.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], establezca este atributo en la subpropiedad **Safe Against Script** de la propiedad **Safe Control Entries** del elemento de proyecto.  Para obtener más información, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) y [Cómo: Marcar los controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md).  
  
## Control de cuentas de usuario de Windows Vista y Windows 7  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporan una característica de seguridad denominada Control de cuentas de usuario \(UAC\).  Para poder desarrollar soluciones de SharePoint mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sistemas [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], UAC requiere que se ejecute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como administrador del sistema.  En el menú de **Comienzo** , abra el menú contextual para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]y, a continuación **Ejecutar como administrador**.  
  
 Para configurar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para atajar para ejecutarse siempre como administrador, abra el menú contextual, elija **Propiedades**, elija el botón de **opciones avanzadas** en el cuadro de diálogo de **Propiedades** , seleccione la casilla de **Ejecutar como administrador** .  
  
 Para obtener más información, vea [Descripción y configuración del Control de cuentas de usuario en Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476) y [Control de cuentas de usuario de Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).  
  
## Consideraciones sobre los permisos de SharePoint  
 Para desarrollar las soluciones de SharePoint, debe tener los permisos necesarios para ejecutar y depurar soluciones de SharePoint.  Antes de probar una solución de SharePoint, dé los pasos siguientes para asegurarse de que tiene los permisos necesarios:  
  
1.  Agregue su cuenta de usuario como administrador del sistema.  
  
2.  Agregue su cuenta de usuario como administrador del conjunto de servidores en el servidor de SharePoint.  
  
    1.  En Administración central de SharePoint 2010, elija el vínculo de **Administrar el grupo administradores de la granja** .  
  
    2.  En la página de **Administradores de la granja** , elija la opción de menú de **new**  
  
3.  Agregue su cuenta de usuario al grupo WSS\_ADMIN\_WPG.  
  
## Recursos de seguridad adicionales  
 Para obtener más información sobre problemas de seguridad, vea las páginas siguientes:  
  
### Seguridad de Visual Studio  
  
-   [Seguridad y permisos de usuario](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [Seguridad en código nativo y el código de .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [Seguridad en .NET Framework](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### Seguridad de SharePoint  
  
-   [Base Administración de SharePoint y seguridad](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [Centro de recursos de seguridad de SharePoint](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [Protección de elementos web en la base de SharePoint](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Mejora de seguridad de aplicación web: Amenazas y medidas](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### Seguridad general  
  
-   [Ciclo de vida de desarrollo de la seguridad de MSDN](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [Compilar aplicaciones seguras de ASP.NET: Autenticación, Autorización, y comunicación](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  