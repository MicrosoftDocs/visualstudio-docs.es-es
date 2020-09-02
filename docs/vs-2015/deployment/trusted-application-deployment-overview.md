---
title: Información general sobre la implementación de aplicaciones de confianza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 673cc3d9b936131e6423a015af5c78486846fbe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847707"
---
# <a name="trusted-application-deployment-overview"></a>Trusted Application Deployment Overview
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se proporciona información general sobre cómo implementar aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que disponen de permisos elevados usando la tecnología de implementación de aplicaciones de confianza.  
  
 La implementación de aplicaciones de confianza, que forma parte de la tecnología de implementación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , facilita a empresas de cualquier tamaño la concesión de permisos adicionales a una aplicación administrada, de forma más segura y sin intervención del usuario. Con la implementación de aplicaciones de confianza, una empresa puede simplemente configurar un equipo cliente para que disponga de una lista de editores de confianza identificados mediante certificados Authenticode. A partir de ese momento, toda aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] firmada por uno de estos editores de confianza recibirá un mayor nivel de confianza.  
  
> [!NOTE]
> La implementación de aplicaciones de confianza requiere una configuración inicial del equipo de usuario. En entornos de escritorio administrados, esta configuración puede llevarse a cabo usando una directiva global. Si no es lo que desea para la aplicación, use en su lugar la elevación de permisos. Para más información, consulte [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="trusted-application-deployment-basics"></a>Aspectos básicos de la implementación de aplicaciones de confianza  
 En la tabla siguiente se muestran los objetos y los roles involucrados en la implementación de aplicaciones de confianza.  
  
|Objeto o rol|Descripción|  
|--------------------|-----------------|  
|administrator|Entidad de la empresa responsable de la actualización y mantenimiento de los equipos cliente.|  
|administrador de confianza|Subsistema dentro de Common Language Runtime (CLR) responsable de hacer cumplir la seguridad de la aplicación cliente.|  
|publisher|Entidad que escribe y mantiene la aplicación.|  
|implementador|Entidad que empaqueta y distribuye la aplicación a los usuarios.|  
|certificado|Firma criptográfica compuesta por una clave pública y una clave privada; generalmente la emite una entidad de certificación (CA) que puede atestiguar su autenticidad.|  
|certificado Authenticode|Certificado con metadatos insertados que describen, entre otras cosas, la finalidad de dicho certificado.|  
|entidad de certificación|Organización que comprueba la identidad de los editores y les emite certificados insertados con los metadatos del editor.|  
|entidad raíz|Entidad de certificación que autoriza a otras entidades a emitir certificados.|  
|contenedor de claves|Espacio de almacenamiento lógico en Microsoft Windows para almacenar los certificados.|  
|editor de confianza|Editor cuyo certificado de Authenticode se ha agregado a una lista de certificados de confianza (CTL) en un equipo cliente.|  
  
 En organizaciones de mayor tamaño, el editor y el implementador suelen ser entidades independientes:  
  
- El editor es el grupo que se encarga de crear la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
- El implementador es el grupo —normalmente el departamento de la tecnología de la información (TI)— que se encarga de distribuir la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a los equipos de escritorio de empresas corporativas.  
  
  Siga estos pasos para aprovechar las ventajas de la implementación de aplicaciones de confianza:  
  
1. Obtenga un certificado para el editor.  
  
2. Agregue el editor al almacén de editores de confianza en todos los clientes.  
  
3. Cree su aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
4. Firme el manifiesto de implementación con el certificado del editor.  
  
5. Publique la implementación de la aplicación en los equipos cliente.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Obtener un certificado para el editor  
 Los certificados digitales son un componente básico de la autenticación Microsoft Authenticode y del sistema de seguridad. Authenticode es un elemento estándar del sistema operativo Windows. Todas las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] deben firmarse con un certificado digital, independientemente de que participen en la implementación de aplicaciones de confianza. Para obtener una explicación completa del funcionamiento de Authenticode con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , consulte [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Agregar el editor al almacén de editores de confianza  
 Para que la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] reciba un mayor nivel de confianza, deberá agregar el certificado como editor de confianza a cada uno de los equipos cliente donde vaya a ejecutarse la aplicación. La realización de esta tarea se compone de una única configuración. Una vez realizada, podrá implementar todas las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] firmadas que desee con el certificado del editor, y todas ellas se ejecutarán con un alto nivel de confianza.  
  
 Si está implementando la aplicación en un entorno de escritorio administrado —por ejemplo, una intranet empresarial donde se ejecute el sistema operativo Windows—, podrá agregar editores de confianza al almacén de un cliente creando una nueva lista de certificados de confianza (CTL) con la directiva de grupo. Para obtener más información, consulte [Create a certificate trust list for a Group Policy object](https://technet.microsoft.com/library/2c03582f-00b2-43e5-ae1d-493894ad0fd7)(Crear una lista de certificados de confianza para un objeto de directiva de grupo).  
  
 Si no está implementando la aplicación en un entorno de escritorio administrado, dispone de las siguientes opciones para agregar un certificado al almacén de editores de confianza:  
  
- El espacio de nombres <xref:System.Security.Cryptography?displayProperty=fullName> .  
  
- CertMgr.exe, que es un componente de Internet Explorer y, por tanto, existe en Windows 98 y en todas las versiones posteriores. Para obtener más información, vea [Certmgr.exe (herramienta de administración de certificados)](https://msdn.microsoft.com/library/7e953b43-1374-4bbc-814f-53ca1b6b52bb).  
  
### <a name="create-a-clickonce-application"></a>Crear una aplicación ClickOnce  
 Una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] es una aplicación cliente [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] combinada con archivos de manifiesto que describen la aplicación y proporcionan parámetros de instalación. Puede convertir el programa en una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] con el comando **Publicar** de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Otra opción es generar todos los archivos necesarios para la implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mediante las herramientas incluidas en el [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Para obtener pasos detallados sobre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación, consulte [Tutorial: Implementación manual de una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 La implementación de aplicaciones de confianza es específica de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]y solo puede usarse con aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
### <a name="sign-the-deployment"></a>Firmar la implementación  
 Una vez obtenido el certificado, debe usarlo para firmar la implementación. Si está implementando la aplicación mediante el asistente para publicación de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , el asistente generará automáticamente un certificado de prueba en caso de que no haya especificado ningún certificado. También puede usar la ventana Diseñador de proyectos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para suministrar un certificado proporcionado por una entidad de certificación.  Consulte también [Cómo: Publicar una aplicación ClickOnce sin usar el Asistente para publicación](https://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) o [Cómo: Publicar una aplicación ClickOnce con el Asistente para publicación](https://msdn.microsoft.com/library/31kztyey\(v=vs.110\)).  
  
> [!CAUTION]
> No le recomendamos implementar la aplicación con un certificado de prueba.  
  
 También puede firmar la aplicación mediante las herramientas del SDK Mage.exe o MageUI.exe. Para obtener más información, vea [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Para obtener una lista completa de las opciones de línea de comandos relacionadas con la firma de implementación, vea [Mage.exe (herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
### <a name="publish-the-application"></a>Publicación de la aplicación  
 En cuanto haya firmado los manifiestos de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , la aplicación estará lista para publicarse en la ubicación de instalación. La ubicación de instalación puede ser un servidor web, un recurso compartido de archivos o el disco local. Cuando un cliente tiene acceso al manifiesto de implementación por primera vez, el administrador de confianza debe elegir si un editor de confianza instalado ha concedido a la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] autoridad para ejecutarse en un nivel de confianza superior. El administrador de confianza realiza esta elección comparando el certificado usado para firmar la implementación con los certificados almacenados en el almacén de editores de confianza del cliente. Si el administrador de confianza encuentra alguna coincidencia, la aplicación se ejecuta con un alto nivel de confianza.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Implementación de aplicaciones de confianza y elevación de permisos  
 Si el editor actual no es un editor de confianza, el administrador de confianza usará la elevación de permisos para preguntar al usuario si desea conceder permisos elevados a la aplicación. No obstante, si el administrador deshabilita la elevación de permisos, la aplicación no podrá obtener permiso para ejecutarse. La aplicación no se ejecutará y no se mostrará ninguna notificación al usuario. Para obtener más información sobre la elevación de permisos, vea [proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Limitaciones de la implementación de aplicaciones de confianza  
 Puede usar la implementación de aplicaciones de confianza para conceder una confianza elevada a las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementadas en la Web o en un recurso compartido de archivos de la empresa. No es necesario que use la implementación de aplicaciones de confianza para las aplicaciones [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que se distribuyen en un CD porque, de forma predeterminada, estas aplicaciones gozan de plena confianza.  
  
## <a name="see-also"></a>Consulte también  
 [Mage.exe (Herramienta de generación y edición de manifiestos)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Tutorial: Implementación manual de una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
