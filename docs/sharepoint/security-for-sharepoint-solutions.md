---
title: Seguridad para las soluciones de SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc1449a40528670274ea5b275cca3f0a8d2f277
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983775"
---
# <a name="security-for-sharepoint-solutions"></a>Seguridad para las soluciones de SharePoint
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incorpora las siguientes características para ayudar a mejorar la seguridad de las aplicaciones de SharePoint.

## <a name="safe-control-entries"></a>Entradas de control seguras
 Cada elemento de proyecto de SharePoint creado en [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene una propiedad **Safe control entries** que representa una colección de controles seguros. Su subpropiedad **Safe** le permite especificar los controles que considera seguros. Para obtener más información, vea [proporcionar información de paquete e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) y [especificar el elementos Web seguro](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers (atributo)
 De forma predeterminada, solo las aplicaciones que son de plena confianza para el sistema de seguridad de acceso del código (CAS) en tiempo de ejecución pueden tener acceso a un ensamblado de código administrado compartido. Marcar un ensamblado de plena confianza con el atributo AllowPartiallyTrustedCallers permite a los ensamblados de confianza parcial tener acceso a él.

 El atributo AllowPartiallyTrustedCallers se agrega a cualquier solución de SharePoint que no esté implementada en la caché global de ensamblados del sistema ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Esto incluye soluciones en espacio aislado o soluciones implementadas en el directorio bin de la aplicación de SharePoint. Para obtener más información, vea [cambios de seguridad de la versión 1 para el marco de Microsoft .net](/previous-versions/msp-n-p/ff921345(v=pandp.10)) e [implementar elementos Web en SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Safe contra la propiedad de script
 La *inyección de script* es la inserción de código potencialmente malintencionado en controles o páginas Web. Para ayudar a proteger los sitios de SharePoint 2010 contra la inyección de scripts, los colaboradores no pueden ver ni editar elementos Web o sus propiedades de forma predeterminada. Este comportamiento se controla mediante un atributo SafeControl denominado SafeAgainstScript. En [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], establezca este atributo en la subpropiedad seguridad de **las entradas de control seguras** de un elemento de proyecto en el **script**. Para obtener más información, vea [proporcionar información de paquete e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) y [Cómo: marcar los controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Control de cuentas de usuario de vista y Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporan una característica de seguridad conocida como control de cuentas de usuario (UAC). Para poder desarrollar soluciones de SharePoint mediante [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] en sistemas [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] y [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], UAC requiere que se ejecute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como administrador del sistema. En el menú **Inicio** , abra el menú contextual de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]y, a continuación, elija **Ejecutar como administrador**.

 Para configurar el acceso directo de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para que siempre se ejecute como administrador, abra el menú contextual, elija **propiedades**, elija el botón **Opciones avanzadas** en el cuadro de diálogo **propiedades** y, a continuación, active la casilla **Ejecutar como administrador** .

 Para obtener más información, consulte [Descripción y configuración del control de cuentas de usuario en Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). y el [control de cuentas de usuario de Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Consideraciones sobre los permisos de SharePoint
 Para desarrollar las soluciones de SharePoint, debe tener los permisos necesarios para ejecutar y depurar soluciones de SharePoint. Antes de probar una solución de SharePoint, dé los pasos siguientes para asegurarse de que tiene los permisos necesarios:

1. Agregue su cuenta de usuario como administrador del sistema.

2. Agregue su cuenta de usuario como administrador del conjunto de servidores en el servidor de SharePoint.

    1. En administración central de SharePoint 2010, elija el vínculo **administrar el grupo administradores del conjunto de servidores** .

    2. En la página administradores de la **granja de servidores** , elija la opción de menú **nuevo** .

3. Agregue su cuenta de usuario al grupo WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Recursos de seguridad adicionales
 Para obtener más información acerca de los problemas de seguridad, consulte lo siguiente.

### <a name="visual-studio-security"></a>seguridad en Visual Studio

- [Seguridad y permisos de usuario](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Seguridad en código nativo y .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Seguridad en .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Seguridad de SharePoint

- [Administración y seguridad de SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Centro de recursos de seguridad de SharePoint](/sharepoint/dev/)

- [Proteger elementos web en SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Mejorar la seguridad de las aplicaciones web: amenazas y contramedidas](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Seguridad general

- [Ciclo de vida de desarrollo de seguridad de MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Creación de aplicaciones de ASP.NET seguras: autenticación, autorización y comunicación segura](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Vea también

- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)