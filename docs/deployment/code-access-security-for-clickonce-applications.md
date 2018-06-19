---
title: Seguridad de acceso del código para aplicaciones ClickOnce | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dad9b3c8391c54c4d668a4c695f4f459664ef373
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560718"
---
# <a name="code-access-security-for-clickonce-applications"></a>Seguridad de acceso del código para aplicaciones ClickOnce
Las aplicaciones ClickOnce se basan en .NET Framework y están sujetas a restricciones de seguridad de acceso del código. Por esta razón, es importante que comprenda las implicaciones de la seguridad de acceso del código y escriba las aplicaciones ClickOnce en consecuencia.  
  
 La seguridad de acceso del código es un mecanismo de .NET Framework que ayuda a limitar el acceso que el código tiene a recursos y operaciones protegidos. Debe configurar los permisos de seguridad de acceso del código para la aplicación ClickOnce para que use la zona correspondiente a la ubicación del instalador de la aplicación. En la mayoría de los casos, puede elegir la zona **Internet** para un conjunto limitado de permisos o la zona **Intranet local** para un conjunto mayor de permisos.  
  
## <a name="default-clickonce-code-access-security"></a>Seguridad de acceso del código de ClickOnce predeterminada  
 De forma predeterminada, una aplicación ClickOnce recibe permisos de plena confianza cuando se instala o ejecuta en un equipo cliente.  
  
-   Una aplicación que tenga permisos de plena confianza tendrá acceso sin restricciones a recursos como el sistema de archivos y el registro. Potencialmente, esto permite que a la aplicación (y el sistema del usuario final) sea susceptible a un ataque de software malintencionado.  
  
-   Cuando una aplicación requiere permisos de plena confianza, puede que se pida al usuario final que conceda permisos a la aplicación. Esto significa que la aplicación no proporciona realmente una experiencia ClickOnce y el mensaje de solicitud puede resultar confuso para los usuarios menos experimentados.  
  
    > [!NOTE]
    >  Al instalar una aplicación desde medios extraíbles, como puede ser un CD-ROM, no se realiza ninguna solicitud al usuario. Además, un administrador de red puede configurar la directiva de red para que no se realicen solicitudes a los usuarios al instalar una aplicación desde un origen de confianza. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
 Para restringir los permisos de una aplicación ClickOnce, puede modificar los permisos de seguridad de acceso del código de la aplicación para que solicite la zona que mejor se adapte a los permisos que requiera la aplicación. En la mayoría de los casos, puede seleccionar la zona desde la que se implementa la aplicación. Por ejemplo, si la aplicación es una aplicación empresarial, puede usar la zona **Intranet local** . Si la aplicación es una aplicación de Internet, puede usar la zona **Internet** .  
  
## <a name="configuring-security-permissions"></a>Configurar permisos de seguridad  
 Siempre debe configurar la aplicación ClickOnce para que solicite la zona correcta para limitar los permisos de seguridad de acceso del código. Puede configurar los permisos de seguridad en la página **Seguridad** del **Diseñador de proyectos**.  
  
 La página **Seguridad** del **Diseñador de proyectos** contiene la casilla **Habilitar la configuración de seguridad ClickOnce** . Cuando esta casilla está activada, se agregan solicitudes de permiso de seguridad al manifiesto de implementación de la aplicación. Durante la instalación, se pedirá al usuario que conceda permisos si los permisos solicitados superan los permisos predeterminados para la zona desde la que se implementa la aplicación. Para obtener más información, consulta [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md).  
  
 A las aplicaciones implementadas desde diferentes ubicaciones se les conceden distintos niveles de permisos sin preguntar. Por ejemplo, cuando una aplicación se implementa desde Internet, recibe un conjunto de permisos muy restrictivo. Cuando se instala desde una Intranet local, recibe más permisos y cuando se instala desde un CD-ROM, recibe permisos de plena confianza.  
  
 Como punto de partida para configurar los permisos, puede seleccionar una zona de seguridad de la lista **Zona** de la página **Seguridad** . Si es probable que la aplicación se implemente desde más de una zona, seleccione la zona con menos permisos. Para obtener más información, consulta [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).  
  
 Las propiedades que se pueden establecer varían según el conjunto de permisos; no todos los conjuntos de permisos tienen propiedades configurables. Para obtener más información acerca de la lista completa de permisos que pueda solicitar su aplicación, consulte <xref:System.Security.Permissions>. Para obtener más información sobre cómo establecer permisos para una zona personalizada, consulte [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>Depurar una aplicación que tiene permisos restringidos  
 Como desarrollador, lo más probable es que ejecute su equipo de desarrollo con permisos de plena confianza. Por tanto, no verá las mismas excepciones de seguridad al depurar la aplicación que puede que vean los usuarios al ejecutarla con permisos restringidos.  
  
 Para detectar estas excepciones, debe depurar la aplicación con los mismos permisos que el usuario final. Se puede habilitar la depuración con permisos restringidos en la página **Seguridad** del **Diseñador de proyectos**.  
  
 Cuando depura una aplicación con permisos restringidos, se generan excepciones para cualquier demanda de seguridad del código que no se haya habilitado en la página **Seguridad** . Aparecerá una aplicación auxiliar de excepciones proporcionando sugerencias sobre cómo modificar el código para evitar que se produzca la excepción.  
  
 Además, cuando escribe código, la característica IntelliSense del Editor de código deshabilitará cualquier miembro que no esté incluido en los permisos de seguridad que haya configurado.  
  
 Para obtener más información, consulta [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>Permisos de seguridad para las aplicaciones hospedadas en explorador  
 Visual Studio proporciona los siguientes tipos de proyecto para las aplicaciones de Windows Presentation Foundation (WPF):  
  
-   Aplicación Windows WPF  
  
-   Aplicación de explorador web WPF  
  
-   Biblioteca de controles personalizados WPF  
  
-   Biblioteca de servicios WPF  
  
 De estos tipos de proyectos, solo las aplicaciones de explorador web WPF se hospedan en un explorador web y, por tanto, requieren una implementación y una configuración de seguridad especiales. La configuración de seguridad predeterminada para estas aplicaciones es la siguiente:  
  
-   **Habilitar la configuración de seguridad ClickOnce**  
  
-   **Esta es una aplicación de confianza parcial**  
  
-   **Zona de Internet** (con el permiso predeterminado establecido para aplicaciones de explorador web WPF seleccionado)  
  
 En el cuadro de diálogo **Configuración de seguridad avanzada** , la casilla **Depurar esta aplicación con el conjunto de permisos seleccionados** está activada y deshabilitada. Esto se debe a que no se puede desactivar Depurar en zona para aplicaciones hospedadas en explorador.  
  
## <a name="see-also"></a>Vea también  
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Cómo: Habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)   
 [Página Seguridad, Diseñador de proyectos](../ide/reference/security-page-project-designer.md)