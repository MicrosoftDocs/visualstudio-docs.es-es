---
title: Proteger soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd86b7c15fa198b37ce15c75b13d2863f56ca3ba
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693375"
---
# <a name="secure-office-solutions"></a>Proteger soluciones de Office
  El modelo de seguridad para soluciones de Office incluye varias tecnologías: la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], el centro de confianza de Microsoft Office y la zona de sitios restringidos de Internet Explorer. En las secciones siguientes se describe el funcionamiento de las distintas características de seguridad:  
  
-   [Conceder confianza a las soluciones de Office](#GrantingTrustToSolutions)  
  
-   [Conceder confianza a documentos](#GrantingTrustToDocuments)  
  
-   [Otorgar confianza al usar Windows Installer](#GrantingTrustWindowsInstaller)  
  
-   [Consideraciones de seguridad específicas para soluciones de Office](#Security)  
  
-   [Seguridad durante el desarrollo](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools para Office runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Conceder confianza a las soluciones de Office  
 Otorgar confianza a las soluciones de Office significa modificar la directiva de seguridad de cada usuario final para que se confíe en la solución de Office basándose en la evidencia siguiente:  
  
-   El certificado usado para firmar el manifiesto de implementación.  
  
-   La URL del manifiesto de implementación.  
  
 Para obtener más información, consulte [conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Conceder confianza a documentos  
 Una personalización de nivel de documento requiere que el documento esté en un directorio designado como ubicación de confianza. Para obtener más información, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Otorgar confianza al usar Windows Installer  
 Con Windows Installer puede crear un archivo MSI para instalar soluciones de Office en el directorio Archivos de programa, lo que requiere derechos de administrador. Para las soluciones de Office en el directorio de archivos de programa, Visual Studio 2010 Tools para Office runtime considera que estas soluciones de Office que sea de confianza y no se muestra el aviso de confianza de ClickOnce.  
  
##  <a name="Security"></a> Consideraciones de seguridad específicas para soluciones de Office  
 Las características de seguridad proporcionadas por [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] y Microsoft Office pueden contribuir en la protección contra diversas amenazas de seguridad en soluciones de Office. Para obtener más información, consulte [consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Seguridad durante el desarrollo  
 Para facilitar el proceso de desarrollo, cada vez que se compila un proyecto Visual Studio establece la directiva de seguridad que se necesita para ejecutar y depurar la solución en el equipo. En algunos casos deberá tomar medidas de seguridad adicionales para desarrollar el proyecto.  
  
### <a name="document-level-solutions"></a>Soluciones de nivel de documento  
 La ruta de acceso completa de un documento debe agregarse a la lista de ubicaciones de confianza en la aplicación de Microsoft Office si va a desarrollar los siguientes tipos de proyectos:  
  
-   Soluciones que se encuentran en un recurso compartido de red como de nivel de documento  *\\\servername\sharename*.  
  
-   Soluciones de nivel de documento para Word que usan *.doc* o *.docm* archivos.  
  
 Incluya los subdirectorios cuando agregue la ubicación del documento a la lista de ubicaciones de confianza, o incluya específicamente las carpetas de depuración y compilación. Para obtener más información, vea el artículo de ayuda en línea de Microsoft Office [crear, quitar o cambiar una ubicación de confianza para los archivos](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Certificados temporales  
 Visual Studio crea un certificado temporal si no existe ya un certificado de firma. Use este certificado temporal únicamente durante el desarrollo y adquiera un certificado oficial para la implementación.  
  
 El certificado temporal se genera después de compilar por vez primera un proyecto de Office. La próxima vez que presione **F5**, se vuelve a generar el proyecto porque el proyecto se marca como modificado al agregar el certificado.  
  
 Los certificados temporales pueden acumularse pasado un tiempo, por lo que se recomienda borrarlos de vez en cuando.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools para Office runtime  
 El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tiene características que comprueban la identidad del publicador y los permisos concedidos a una personalización. Estos permisos se comprueban mediante una secuencia de comprobaciones de seguridad.  
  
### <a name="security-during-customization-loading"></a>Seguridad durante la carga de personalización  
 Cuando se carga una personalización de nivel de documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] siempre comprueba si el documento está en la lista de ubicaciones de confianza. Además, el tiempo de ejecución comprueba si la solución requiere el permiso FullTrust en el manifiesto de aplicación. Mientras se carga la personalización, no realiza ninguna otra comprobación de seguridad.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Secuencia de comprobaciones de seguridad durante la instalación  
 Cuando una solución de Office se instala o actualiza, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] realiza una serie de comprobaciones de seguridad en una secuencia concreta para tomar una decisión de confianza. Una solución solo se instala o actualiza si el runtime determina que es de confianza.  
  
 Puede iniciar el proceso de instalación de cuatro maneras: ejecutando el programa de instalación, abriendo el manifiesto de implementación, abriendo el host de aplicación de Microsoft Office o ejecutando *VSTOInstaller.exe*.  
  
 La primera comprobación de seguridad tan solo se aplica a las soluciones de nivel de documento. El documento de una solución de nivel de documento debe estar en una ubicación de confianza. Si el documento se encuentra en un recurso compartido de archivos de red remota o si tiene un *.doc* o *.docm* extensión, la ubicación del documento debe agregarse a la lista de ubicaciones de confianza. Para obtener más información, consulte [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).  
  
 ![Seguridad de VSTO: instalar desde Microsoft Office](../vsto/media/host-install.png "seguridad de VSTO: instalar desde Microsoft Office")  
  
 El siguiente conjunto de comprobaciones de seguridad son de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y ClickOnce. Para pasar estas comprobaciones, las soluciones de Office deben solicitar permisos FullTrust, estar firmadas con un certificado que no aparece en la lista de editores de confianza y estar en una ubicación que no está en la zona restringida de Internet Explorer. Si el certificado está en la lista de editores de confianza, la solución se instala inmediatamente. En caso contrario, si no produjo error en ninguna de las comprobaciones, la solución avanza hasta el conjunto final de las comprobaciones.  
  
 ![Seguridad de VSTO para instalar soluciones](../vsto/media/installing.png "seguridad de VSTO para instalar soluciones")  
  
 Si el [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] se permite el aviso de confianza y la solución aún no se ha concedido confianza, el tiempo de ejecución permitirá que la decisión de confianza ser realizados por el usuario final. Si el usuario concede confianza a la solución, se agrega una entrada a la lista de inclusión del usuario. Todas las soluciones de la lista de inclusión del usuario tienen plena confianza y pueden instalarse y ejecutarse.  
  
 A partir de Visual Studio 2010, la lista de inclusión se omite si la solución de Office se instala mediante Windows Installer (MSI) en el directorio Archivos de programa. Para obtener más información, consulte [soluciones de Office de confianza mediante el uso de listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Seguridad de VSTO: usar el programa de instalación para instalar](../vsto/media/setup-vstoinstaller.png "seguridad de VSTO: usar el programa de instalación para instalar")  
  
## <a name="see-also"></a>Vea también  
 [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Conceder confianza a documentos](../vsto/granting-trust-to-documents.md)   
 [Confiar en soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Cómo: configurar la seguridad de la lista de inclusión](../vsto/how-to-configure-inclusion-list-security.md)   
 [Cómo: firmar soluciones de Office](../vsto/how-to-sign-office-solutions.md)   
 [Solucionar problemas de seguridad de la solución de Office](../vsto/troubleshooting-office-solution-security.md)   
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Referencia de ClickOnce](/visualstudio/deployment/clickonce-reference)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  