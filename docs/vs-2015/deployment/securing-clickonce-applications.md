---
title: Proteger las aplicaciones ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ae5bd70a675798d971cb184038a7e036d04fc95a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247226"
---
# <a name="securing-clickonce-applications"></a>Proteger las aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las aplicaciones[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] están sujetas a las restricciones en materia de seguridad de acceso del código de .NET Framework para ayudar a limitar el acceso del código a los recursos y operaciones protegidos. Por esta razón, es importante que comprenda las implicaciones de la seguridad de acceso del código para que pueda escribir las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] en consecuencia. Las aplicaciones pueden utilizar Plena confianza o zonas parciales, como las zonas de Internet o intranet, para limitar el acceso.  
  
 Además, ClickOnce utiliza certificados para comprobar la autenticidad del publicador de la aplicación y firmar los manifiestos de aplicación e implementación a fin de demostrar que los archivos no se han alterado. La firma es un paso opcional, que facilita la modificación de los archivos de la aplicación una vez que se han generado los manifiestos. Sin embargo, sin manifiestos firmados, es difícil garantizar que el instalador de la aplicación no ha sido manipulado a través de ataques de seguridad de tipo "Man in the middle". Por este motivo, le recomendamos que firme la aplicación y los manifiestos de implementación, lo que le ayudará a proteger las aplicaciones.  
  
## <a name="zones"></a>Zonas  
 Las aplicaciones que se implementan mediante la tecnología [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se limitan a un conjunto de permisos y acciones definidos por la zona de seguridad. Las zonas de seguridad se definen en Internet Explorer y se basan en la ubicación de la aplicación. En la tabla siguiente se muestran los permisos predeterminados basados en la ubicación de la implementación:  
  
|Ubicación de la implementación|Zona de seguridad|  
|-------------------------|-------------------|  
|Ejecutada desde el Web|Zona de Internet|  
|Instalada desde el Web|Zona de Internet|  
|Instalada desde un recurso compartido de archivos de red|Zona de intranet local|  
|Instalada desde un CD-ROM|Plena confianza|  
  
 Los permisos predeterminados se basan en la ubicación desde la cual fue implementada la versión original de la aplicación; las actualizaciones de la aplicación heredarán esos permisos. Si la aplicación se configura para que compruebe las actualizaciones desde una ubicación web o una ubicación de red y se encuentra disponible una versión más reciente, la instalación original puede recibir permisos para Internet o para la zona Intranet en lugar de permisos de plena confianza. Para evitar que el programa pida a los usuarios que concedan los permisos, el administrador del sistema puede especificar una directiva de implementación ClickOnce que defina un editor de aplicación concreto como origen de confianza. Para aquellos equipos en los que se implemente esta directiva, los permisos se concederán automáticamente y no se preguntará al usuario. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Para configurar la implementación de aplicaciones de confianza, el certificado puede instalarse en el equipo o en el nivel de empresa. Para obtener más información, consulta [Cómo: Agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Directivas de seguridad de acceso del código  
 Se determinan los permisos para una aplicación mediante la configuración de la [ \<trustInfo > elemento](../deployment/trustinfo-element-clickonce-application.md) elemento del manifiesto de aplicación. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera automáticamente esta información según la configuración de la página de propiedades **Seguridad** del proyecto. A una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] solo se le conceden los permisos específicos que solicita. Por ejemplo, cuando el acceso a archivos requiere permisos de plena confianza, si la aplicación solicita permiso de acceso al archivo, sólo se le concederá permiso de acceso al archivo, pero no permisos de plena confianza. Al desarrollar la aplicación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , debe asegurarse de solicitar solo los permisos específicos que la aplicación necesita. En la mayoría de los casos, puede usar zonas de Internet o intranet local para limitar la aplicación a confianza parcial. Para obtener más información, consulta [Cómo: Establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Si la aplicación requiere permisos personalizados, puede crear una zona personalizada. Para obtener más información, consulta [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Incluso un permiso que no forma parte del conjunto de permisos predeterminado para la zona desde la que se implementa la aplicación hará que al usuario final se le solicite conceder el permiso en el momento de la instalación o actualización. Para evitar que el programa pida a los usuarios que concedan los permisos, el administrador del sistema puede especificar una directiva de implementación ClickOnce que defina un editor de aplicación concreto como origen de confianza. En aquellos equipos en los que se implemente esta directiva, los permisos se concederán automáticamente y no se preguntará al usuario.  
  
 Como desarrollador, es su responsabilidad asegurarse de que la aplicación se ejecute con los permisos adecuados. Si la aplicación solicita permisos fuera de una zona en tiempo de ejecución, es posible que se produzca una excepción de seguridad. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] permite depurar la aplicación en la zona de seguridad de destino. y proporciona ayuda para desarrollar aplicaciones seguras. Para obtener más información, consulta [Cómo: Depurar una aplicación ClickOnce con permisos restringidos](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Para obtener más información sobre la seguridad de acceso del código y ClickOnce, vea [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certificados de firma de código  
 Para publicar una aplicación mediante la implementación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , puede firmar la aplicación y los manifiestos de implementación de la aplicación con un par de clave pública y clave privada. Las herramientas para firmar un manifiesto están disponibles en la página **Firma** del **Diseñador de proyectos**. Para obtener más información, consulta [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md). O bien, puede firmar los manifiestos con un archivo de claves durante el proceso de publicación, mediante el Asistente para publicación.  
  
 Una vez firmados los manifiestos, la información del publicador basada en la firma Authenticode aparecerá ante el usuario en el cuadro de diálogo de permisos, para mostrarle que la aplicación procede de un origen de confianza.  
  
 Para obtener más información sobre ClickOnce y los certificados, vea [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Autenticación basada en formularios de ASP.NET  
 Si desea controlar las implementaciones a las que puede obtener acceso cada usuario, no debe permitir accesos anónimos a las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementadas en un servidor web. En lugar de ello, podría permitir que los usuarios tuvieran acceso a las implementaciones instaladas mediante una identidad de usuario (a través de la autenticación de Windows).  
  
 Sin embargo, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no admite la autenticación basada en formularios de ASP.NET porque usa cookies persistentes; estas representan un riesgo de seguridad porque residen en la memoria caché de Internet Explorer y podrían prestarse a intrusiones. Por lo tanto, si está implementando aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , no se admitirá ningún escenario de implementación que no presente autenticación de Windows.  
  
## <a name="passing-arguments"></a>Pasar argumentos  
 Hay una consideración de seguridad adicional que debe tener en cuenta si necesita pasar argumentos a una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] permite a los desarrolladores proporcionar una cadena de consulta a las aplicaciones implementadas a través de Internet. La cadena de consulta toma la forma de una serie de pares de nombre y valor al final de la dirección URL que se utiliza para iniciar la aplicación:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Los argumentos de la cadena de consulta están deshabilitados de forma predeterminada. Para habilitarlos, debe establecer el atributo `trustUrlParameters` en el manifiesto de implementación de la aplicación. Este valor se puede establecer en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y en MageUI.exe. Para obtener instrucciones detalladas sobre cómo habilitar pasar cadenas de consulta, vea [Cómo: recuperar información de cadena de consulta en una aplicación ClickOnce en línea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 No debe pasar nunca argumentos recuperados a través de una cadena de consulta a una base de datos o a la línea de comandos sin antes comprobar los argumentos para garantizar que sean seguros. No son seguros los argumentos que incluyen caracteres de escape de línea de comandos o base de datos que pueden permitir a un usuario malintencionado manipular la aplicación mediante la ejecución de comandos arbitrarios.  
  
> [!NOTE]
>  Los argumentos de la cadena de consulta constituyen la única forma de pasar argumentos a una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] cuando se inicia. No se pueden pasar argumentos a una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] desde la línea de comandos.  
  
## <a name="deploying-obfuscated-assemblies"></a>Implementar ensamblados protegidos  
 Es posible que desee proteger su aplicación mediante Dotfuscator para impedir el uso de técnicas de ingeniería inversa en el código por parte de otras personas. Sin embargo, la protección de ensamblados no está integrada en el IDE de Visual Studio ni en el proceso de implementación ClickOnce. Por lo tanto, tendrá que encargarse de la protección fuera del proceso de implementación, posiblemente utilizando un paso posterior a la compilación. Una vez compilado el proyecto, tendría que llevar a cabo los siguientes pasos manualmente, fuera de Visual Studio:  
  
1.  Encargarse de la protección mediante Dotfuscator.  
  
2.  Utilizar Mage.exe o MageUI.exe para generar los manifiestos de ClickOnce y firmarlos. Para obtener más información, consulte [Mage.exe (Manifest Generation and Editing Tool)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) y [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
3.  Publicar manualmente (copiar) los archivos en la ubicación de implementación de origen (servidor Web, recurso compartido UNC o CD-ROM).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad e implementación ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



