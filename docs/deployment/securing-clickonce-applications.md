---
title: Proteger las aplicaciones ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56a49bf9cbf2c43cd7692592b53b9aca2b256313
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080345"
---
# <a name="secure-clickonce-applications"></a>Proteger las aplicaciones ClickOnce
Las aplicaciones[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] están sujetas a las restricciones en materia de seguridad de acceso del código de .NET Framework para ayudar a limitar el acceso del código a los recursos y operaciones protegidos. Por esta razón, es importante que comprenda las implicaciones de la seguridad de acceso del código para que pueda escribir las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] en consecuencia. Las aplicaciones pueden utilizar Plena confianza o zonas parciales, como las zonas de Internet o intranet, para limitar el acceso.  
  
 Además, ClickOnce utiliza certificados para comprobar la autenticidad del publicador de la aplicación y firmar los manifiestos de aplicación e implementación a fin de demostrar que los archivos no se han alterado. La firma es un paso opcional, que facilita la modificación de los archivos de la aplicación una vez que se han generado los manifiestos. Sin embargo, sin manifiestos firmados, es difícil garantizar que el instalador de la aplicación no ha sido manipulado a través de ataques de seguridad de tipo "Man in the middle". Por este motivo, le recomendamos que firme la aplicación y los manifiestos de implementación, lo que le ayudará a proteger las aplicaciones.  
  
## <a name="zones"></a>Zonas  
 Las aplicaciones que se implementan mediante la tecnología [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se limitan a un conjunto de permisos y acciones definidos por la zona de seguridad. Las zonas de seguridad se definen en Internet Explorer y se basan en la ubicación de la aplicación. En la tabla siguiente se muestran los permisos predeterminados basados en la ubicación de la implementación:  
  
|Ubicación de la implementación|Zona de seguridad|  
|-------------------------|-------------------|  
|Ejecutada desde el Web|Zona de Internet|  
|Instalada desde el Web|Zona de Internet|  
|Instalada desde un recurso compartido de archivos de red|Zona de intranet local|  
|Instalada desde un CD-ROM|Plena confianza|  
  
 Los permisos predeterminados se basan en la ubicación desde la cual fue implementada la versión original de la aplicación; las actualizaciones de la aplicación heredarán esos permisos. Si la aplicación se configura para que compruebe las actualizaciones desde una ubicación web o una ubicación de red y se encuentra disponible una versión más reciente, la instalación original puede recibir permisos para Internet o para la zona Intranet en lugar de permisos de plena confianza. Para evitar que el programa pida a los usuarios que concedan los permisos, el administrador del sistema puede especificar una directiva de implementación ClickOnce que defina un editor de aplicación concreto como origen de confianza. Para aquellos equipos en los que se implemente esta directiva, los permisos se concederán automáticamente y no se preguntará al usuario. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Para configurar la implementación de aplicaciones de confianza, el certificado puede instalarse en el equipo o en el nivel de empresa. Para obtener más información, consulta [Cómo: Agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Directivas de seguridad de acceso de código  
 Se determinan los permisos para una aplicación mediante la configuración de la [ \<trustInfo > elemento](../deployment/trustinfo-element-clickonce-application.md) elemento del manifiesto de aplicación. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera automáticamente esta información según la configuración de la página de propiedades **Seguridad** del proyecto. A una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solo se le conceden los permisos específicos que solicita. Por ejemplo, cuando el acceso a archivos requiere permisos de plena confianza, si la aplicación solicita permiso de acceso al archivo, sólo se le concederá permiso de acceso al archivo, pero no permisos de plena confianza. Al desarrollar la aplicación de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , debe asegurarse de solicitar solo los permisos específicos que la aplicación necesita. En la mayoría de los casos, puede usar zonas de Internet o intranet local para limitar la aplicación a confianza parcial. Para obtener más información, consulte [Cómo: establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Si la aplicación requiere permisos personalizados, puede crear una zona personalizada. Para obtener más información, consulte [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Incluso un permiso que no forma parte del conjunto de permisos predeterminado para la zona desde la que se implementa la aplicación hará que al usuario final se le solicite conceder el permiso en el momento de la instalación o actualización. Para evitar que el programa pida a los usuarios que concedan los permisos, el administrador del sistema puede especificar una directiva de implementación ClickOnce que defina un editor de aplicación concreto como origen de confianza. En aquellos equipos en los que se implemente esta directiva, los permisos se concederán automáticamente y no se preguntará al usuario.  
  
 Como desarrollador, es su responsabilidad asegurarse de que la aplicación se ejecute con los permisos adecuados. Si la aplicación solicita permisos fuera de una zona en tiempo de ejecución, es posible que se produzca una excepción de seguridad. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite depurar la aplicación en la zona de seguridad de destino. y proporciona ayuda para desarrollar aplicaciones seguras. Para obtener más información, consulte [Cómo: depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Para obtener más información sobre la seguridad de acceso del código y ClickOnce, vea [seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certificados de firma de código  
 Para publicar una aplicación mediante la implementación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , puede firmar la aplicación y los manifiestos de implementación de la aplicación con un par de clave pública y clave privada. Las herramientas para firmar un manifiesto están disponibles en la página **Firma** del **Diseñador de proyectos**. Para obtener más información, consulta [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md). O bien, puede firmar los manifiestos con un archivo de claves durante el proceso de publicación, mediante el Asistente para publicación.  
  
 Una vez firmados los manifiestos, la información del publicador basada en la firma Authenticode aparecerá ante el usuario en el cuadro de diálogo de permisos, para mostrarle que la aplicación procede de un origen de confianza.  
  
 Para obtener más información sobre ClickOnce y los certificados, vea [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Autenticación basada en formularios ASP.NET  
 Si desea controlar las implementaciones a las que puede obtener acceso cada usuario, no debe permitir accesos anónimos a las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementadas en un servidor web. En lugar de ello, podría permitir que los usuarios tuvieran acceso a las implementaciones instaladas mediante una identidad de usuario (a través de la autenticación de Windows).  
  
 Sin embargo,[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] no admite la autenticación basada en formularios de ASP.NET porque usa cookies persistentes; estas representan un riesgo de seguridad porque residen en la memoria caché de Internet Explorer y podrían prestarse a intrusiones. Por lo tanto, si está implementando aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , no se admitirá ningún escenario de implementación que no presente autenticación de Windows.  
  
## <a name="pass-arguments"></a>Pasar argumentos  
 Hay una consideración de seguridad adicional que debe tener en cuenta si necesita pasar argumentos a una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] permite a los desarrolladores proporcionar una cadena de consulta a las aplicaciones implementadas a través de Internet. La cadena de consulta toma la forma de una serie de pares de nombre y valor al final de la dirección URL que se utiliza para iniciar la aplicación:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Los argumentos de la cadena de consulta están deshabilitados de forma predeterminada. Para habilitarlos, debe establecer el atributo `trustUrlParameters` en el manifiesto de implementación de la aplicación. Este valor se puede establecer en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y en MageUI.exe. Para obtener instrucciones detalladas sobre cómo habilitar pasar cadenas de consulta, vea [Cómo: recuperar información de la cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 No debe pasar nunca argumentos recuperados a través de una cadena de consulta a una base de datos o a la línea de comandos sin antes comprobar los argumentos para garantizar que sean seguros. No son seguros los argumentos que incluyen caracteres de escape de línea de comandos o base de datos que pueden permitir a un usuario malintencionado manipular la aplicación mediante la ejecución de comandos arbitrarios.  
  
> [!NOTE]
>  Los argumentos de la cadena de consulta constituyen la única forma de pasar argumentos a una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cuando se inicia. No se pueden pasar argumentos a una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] desde la línea de comandos.  
  
## <a name="deploying-obfuscated-assemblies"></a>Implementar ensamblados protegidos  
 Visual Studio incluye la versión gratuita [PreEmptive Protection - Dotfuscator Community Edition](../ide/dotfuscator/index.md), que puede usar para proteger las aplicaciones ClickOnce a través de ofuscación de código y las medidas de protección activa.  Para obtener más información, consulte [la sección de ClickOnce de la Guía de usuario de Dotfuscator Community Edition](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)