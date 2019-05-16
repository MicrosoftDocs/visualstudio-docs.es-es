---
title: Acceso a datos locales y remotos en las aplicaciones ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ce6b6ee633e926709b0c15c2234077055600a07
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688116"
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>Obtener acceso local o remoto a los datos en aplicaciones ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La mayoría de las aplicaciones consumen o producen los datos. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ofrece diversas opciones para leer y escribir datos, tanto local como remotamente.  
  
## <a name="local-data"></a>Datos locales  
 Con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], puede cargar y almacenar datos localmente usando cualquiera de los métodos siguientes:  
  
- Directorio de datos de[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]   
  
- Almacenamiento aislado  
  
- Otros archivos locales  
  
### <a name="clickonce-data-directory"></a>Directorio de datos de ClickOnce  
 Cada aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalada en un equipo local dispone de un directorio de datos almacenado en la carpeta Documents and Settings del usuario. Todos los archivos incluidos en una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] y marcados como archivos de «datos» se copian en este directorio cuando se instala una aplicación. Los archivos de datos pueden ser de cualquier tipo de archivo; los que se usan con más frecuencia son los archivos de texto, XML y de base de datos, como los archivos .mdb de Microsoft Access.  
  
 El directorio de datos está pensado para los datos administrados de la aplicación, que son datos que la aplicación almacena y mantiene explícitamente. En cambio, todos los archivos estáticos y que no son de dependencia que no estén marcados como «datos» en el manifiesto de aplicación residirán en el directorio de la aplicación. Este directorio es donde residen los archivos ejecutables (.exe) y los ensamblados de la aplicación.  
  
> [!NOTE]
> Cuando se desinstala una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , también se quita su directorio de datos. No use nunca el directorio de datos para almacenar datos administrados del usuario final, como documentos.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>Marcar archivos de datos en una distribución de ClickOnce  
 Para incluir un archivo existente en el directorio de datos, debe marcar dicho archivo como un archivo de datos en el archivo de manifiesto de aplicación de la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Para obtener más información, vea [Cómo: Inclusión de un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Leer y escribir en el directorio de datos  
 Para leer desde el directorio de datos es necesario que la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] solicite permiso de lectura; de forma similar, la escritura en el directorio requiere permiso de escritura. La aplicación tendrá este permiso automáticamente si se configura para que se ejecute con plena confianza. Para obtener más información sobre cómo elevar los permisos de la aplicación mediante el uso de elevación de permisos o implementación de aplicaciones de confianza, consulte [proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
> Si su organización no usa la implementación de aplicaciones de confianza y ha desactivado la elevación de permisos, los permisos de aserción generarán un error.  
  
 Una vez que la aplicación tenga estos permisos, puede acceder al directorio de datos usando llamadas a métodos en clases dentro de <xref:System.IO>. Puede obtener la ruta de acceso al directorio de datos en una aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] de Windows Forms usando la propiedad <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> definida en la propiedad <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> de <xref:System.Deployment.Application.ApplicationDeployment>. Esta es la manera más conveniente y recomendada de acceder a los datos. En el ejemplo de código siguiente se muestra cómo hacer esto en un archivo de texto denominado CSV.txt que ha incluido en la implementación como un archivo de datos.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.OpenDataFile/CS/Form1.cs#1)]
 [!code-vb[ClickOnce.OpenDataFile#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.OpenDataFile/VB/Form1.vb#1)]  
  
 Para obtener más información sobre cómo marcar archivos de la implementación como archivos de datos, vea [Cómo: Inclusión de un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 También puede obtener la ruta de acceso del directorio de datos usando las variables correspondientes de la clase <xref:System.Windows.Forms.Application> , como <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 La manipulación de otros tipos de archivos puede requerir permisos adicionales. Por ejemplo, si desea usar un archivo de base de datos de Access (.mdb), la aplicación debe imponer plena confianza para poder usar las clases <xref:System.Data> correspondientes.  
  
#### <a name="data-directory-and-application-versions"></a>Directorio de datos y versiones de la aplicación  
 Cada versión de una aplicación tiene su propio directorio de datos, que está aislado de otras versiones. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crea este directorio independientemente de si se incluyen archivos de datos en la implementación, de modo que la aplicación tenga una ubicación donde crear nuevos archivos de datos en tiempo de ejecución. Cuando se instala una versión nueva de una aplicación, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] copiará todos los archivos de datos existentes del directorio de datos de la versión anterior en el directorio de datos de la versión nueva, tanto si estaban incluidos en la implementación original como si los creó por la aplicación.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] reemplazará la versión anterior del archivo con la versión más reciente del servidor si un archivo de datos tiene un valor de hash diferente en la versión anterior de la aplicación y en la versión nueva. Además, si la versión anterior de la aplicación creó un archivo nuevo con el mismo nombre que un archivo incluido en la implementación de la versión nueva, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sobrescribirá el archivo de la versión anterior con el archivo nuevo. En ambos casos, los archivos anteriores se incluirán en un subdirectorio del directorio de datos denominado `.pre`, de modo que la aplicación todavía podrá acceder a los datos antiguos para fines de migración.  
  
 Si necesita una migración de datos más precisa, puede usar la API de implementación de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] para realizar la migración personalizada desde el directorio de datos anterior al directorio de datos nuevo. Tendrá que probar una descarga disponible mediante <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, descargar la actualización mediante <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> o <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>y hacer que la migración de datos personalizada funcione en su aplicación una vez finalizada la actualización.  
  
### <a name="isolated-storage"></a>Almacenamiento aislado  
 El almacenamiento aislado proporciona una API para crear y acceder a archivos mediante una API sencilla. La ubicación real de los archivos almacenados está oculta para el desarrollador y el usuario.  
  
 El almacenamiento aislado funciona en todas las versiones de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. El almacenamiento aislado también funciona en aplicaciones de confianza parcial sin necesidad de que se concedan permisos adicionales. Debe usar el almacenamiento aislado si la aplicación debe ejecutarse en confianza parcial, pero debe conservar los datos específicos de la aplicación.  
  
 Para obtener más información, consulta [Almacenamiento aislado](https://msdn.microsoft.com/library/aff939d7-9e49-46f2-a8cd-938d3020e94e).  
  
### <a name="other-local-files"></a>Otros archivos locales  
 Si la aplicación debe funcionar con datos del usuario final o si debe guardar dichos datos, como informes, imágenes, música, etc., la aplicación necesitará <xref:System.Security.Permissions.FileIOPermission> para leer y escribir datos en el sistema de archivos local.  
  
## <a name="remote-data"></a>Datos remotos  
 En algún momento, la aplicación probablemente tendrá que recuperar información de un sitio web remoto, como datos de clientes o información de mercado. En esta sección se describen las técnicas más comunes para recuperar datos remotos.  
  
### <a name="accessing-files-by-using-http"></a>Acceder a archivos mediante HTTP  
 Puede acceder a datos desde un servidor web usando la clase <xref:System.Net.WebClient> o <xref:System.Net.HttpWebRequest> en el espacio de nombres <xref:System.Net> . Los datos pueden ser archivos estáticos o aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que devuelven texto sin formato o datos XML. Si los datos están en formato XML, la forma más rápida de recuperar los datos consiste en usar la clase <xref:System.Xml.XmlDocument> , cuyo método <xref:System.Xml.XmlDocument.Load%2A> toma una dirección URL como argumento. Para obtener un ejemplo, consulta [Reading an XML Document into the DOM](https://msdn.microsoft.com/library/a4fb291f-5630-49ba-a49a-5b66c3b71e49).  
  
 Debe tener en cuenta la seguridad cuando la aplicación acceda a datos remotos a través de HTTP. De forma predeterminada, el acceso de la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a los recursos de red puede estar restringido, en función de cómo se implementase la aplicación. Estas restricciones se aplican para impedir que programas malintencionados obtengan acceso a datos remotos privilegiados o usen el equipo de un usuario para atacar a otros equipos de la red.  
  
 En la tabla siguiente se enumeran las estrategias de implementación que podría usar y sus permisos web predeterminados.  
  
|Tipo de implementación|Permisos de red predeterminados|  
|---------------------|---------------------------------|  
|Instalación web|Solo puede acceder al servidor web desde el que se instaló la aplicación|  
|Instalación de recurso compartido de archivos|No puede acceder a servidores web|  
|Instalación de CD-ROM|Puede acceder a servidores web|  
  
 Si su aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] no puede acceder a un servidor web debido a restricciones de seguridad, la aplicación debe imponer <xref:System.Net.WebPermission> para ese sitio web. Para obtener más información sobre cómo aumentar los permisos de seguridad para un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, consulte [proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Acceder a los datos a través de un servicio web XML  
 Si expone los datos como un servicio web XML, puede acceder a los datos mediante el uso de un proxy de servicio web XML. El proxy es una clase [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que se crea mediante [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Las operaciones del servicio web XML (como recuperar clientes, realizar pedidos, etc.) se exponen como métodos en el proxy. Esto hace que los servicios web sean mucho más fáciles de usar que los archivos XML o de texto sin formato.  
  
 Si el servicio web XML funciona a través de HTTP, el servicio estará sujeto a las mismas restricciones de seguridad que las clases <xref:System.Net.WebClient> y <xref:System.Net.HttpWebRequest> .  
  
### <a name="accessing-a-database-directly"></a>Acceder directamente a una base de datos  
 Puede usar las clases en el espacio de nombres <xref:System.Data> para establecer conexiones directas con un servidor de base de datos como SQL Server en la red, pero debe tener en cuenta las cuestiones de seguridad. A diferencia de las solicitudes HTTP, las solicitudes de conexión de base de datos siempre están prohibidas de manera predeterminada en la confianza parcial; solo obtendrá dichos permisos de forma predeterminada si instala la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] desde un CD-ROM. Esto le concede a la aplicación plena confianza. Para habilitar el acceso a una base de datos de SQL Server específica, la aplicación debe solicitarle <xref:System.Data.SqlClient.SqlClientPermission> ; para habilitar el acceso a una base de datos que no sea SQL Server, debe solicitar <xref:System.Data.OleDb.OleDbPermission>.  
  
 La mayoría de las veces, no tendrá que acceder a la base de datos directamente, sino que lo hará a través de una aplicación de servidor web escrita en [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] o un servicio web XML. Esta forma de acceder a la base de datos suele ser el mejor método si la aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se implementó desde un servidor web. Puede acceder al servidor de confianza parcial sin tener que elevar los permisos de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Inclusión de un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)
