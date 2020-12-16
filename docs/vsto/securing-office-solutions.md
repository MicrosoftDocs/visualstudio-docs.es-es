---
title: Proteger soluciones de Office
description: Obtenga información sobre cómo el modelo de seguridad para las soluciones de Office implica varias tecnologías, incluidas las Visual Studio Tools para Office Runtime y ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bedb49a6d5d17e3c9f79a652183c2b4cd748ff6c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528477"
---
# <a name="secure-office-solutions"></a>Proteger soluciones de Office
  El modelo de seguridad para soluciones de Office implica varias tecnologías: [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , el centro de confianza de Microsoft Office y la zona de sitios restringidos de Internet Explorer. En las secciones siguientes se describe el funcionamiento de las distintas características de seguridad:

- [Conceder confianza a las soluciones de Office](#GrantingTrustToSolutions)

- [Conceder confianza a los documentos](#GrantingTrustToDocuments)

- [Conceder confianza al usar Windows Installer](#GrantingTrustWindowsInstaller)

- [Consideraciones de seguridad específicas para las soluciones de Office](#Security)

- [Seguridad durante el desarrollo](#SecurityDuringDeployment)

- [Runtime de Microsoft Visual Studio Tools para Office](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Conceder confianza a las soluciones de Office
 Otorgar confianza a las soluciones de Office significa modificar la directiva de seguridad de cada usuario final para que se confíe en la solución de Office basándose en la evidencia siguiente:

- El certificado usado para firmar el manifiesto de implementación.

- La URL del manifiesto de implementación.

  Para obtener más información, vea [conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Conceder confianza a los documentos
 Una personalización de nivel de documento requiere que el documento esté en un directorio designado como ubicación de confianza. Para obtener más información, vea [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Conceder confianza al usar Windows Installer
 Con Windows Installer puede crear un archivo MSI para instalar soluciones de Office en el directorio Archivos de programa, lo que requiere derechos de administrador. En el caso de las soluciones de Office en el directorio archivos de programa, el motor en tiempo de ejecución de Visual Studio 2010 Tools para Office considera que estas soluciones de Office son de confianza y no muestra el mensaje de confianza de ClickOnce.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Consideraciones de seguridad específicas para las soluciones de Office
 Las características de seguridad proporcionadas por [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] y Microsoft Office pueden contribuir en la protección contra diversas amenazas de seguridad en soluciones de Office. Para obtener más información, vea [consideraciones de seguridad específicas para soluciones de Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Seguridad durante el desarrollo
 Para facilitar el proceso de desarrollo, cada vez que se compila un proyecto Visual Studio establece la directiva de seguridad que se necesita para ejecutar y depurar la solución en el equipo. En algunos casos deberá tomar medidas de seguridad adicionales para desarrollar el proyecto.

### <a name="document-level-solutions"></a>Soluciones de nivel de documento
 La ruta de acceso completa de un documento debe agregarse a la lista de ubicaciones de confianza en la aplicación de Microsoft Office si va a desarrollar los siguientes tipos de proyectos:

- Soluciones de nivel de documento que se encuentran en un recurso compartido de archivos de red, como *\\ \nombreservidor\nombrerecursocompartido*.

- Soluciones de nivel de documento para Word que usan archivos *. doc* o *. docm* .

  Incluya los subdirectorios cuando agregue la ubicación del documento a la lista de ubicaciones de confianza, o incluya específicamente las carpetas de depuración y compilación. Para obtener más información, vea el artículo de ayuda en pantalla de Microsoft Office [crear, quitar o cambiar una ubicación de confianza para los archivos](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Certificados temporales
 Visual Studio crea un certificado temporal si no existe ya un certificado de firma. Use este certificado temporal únicamente durante el desarrollo y adquiera un certificado oficial para la implementación.

 El certificado temporal se genera después de compilar por vez primera un proyecto de Office. La próxima vez que presione **F5**, el proyecto se volverá a generar porque el proyecto se marca como modificado cuando se agrega el certificado.

 Los certificados temporales pueden acumularse pasado un tiempo, por lo que se recomienda borrarlos de vez en cuando.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools para Office Runtime
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Tiene características para comprobar la identidad del publicador y los permisos que se conceden a una personalización. Estos permisos se comprueban mediante una secuencia de comprobaciones de seguridad.

### <a name="security-during-customization-loading"></a>Seguridad durante la carga de personalización
 Cuando se carga una personalización de nivel de documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] comprueba siempre si el documento se encuentra en la lista de ubicaciones de confianza. Además, el runtime comprueba si la solución requiere el permiso FullTrust en el manifiesto de aplicación. Mientras se carga la personalización, no realiza ninguna otra comprobación de seguridad.

### <a name="sequence-of-security-checks-during-installation"></a>Secuencia de comprobaciones de seguridad durante la instalación
 Cuando una solución de Office se instala o actualiza, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] realiza una serie de comprobaciones de seguridad en una secuencia concreta para tomar una decisión de confianza. Una solución solo se instala o actualiza si el runtime determina que es de confianza.

 Puede iniciar el proceso de instalación de una de estas cuatro maneras: ejecutando el programa de instalación, abriendo el manifiesto de implementación, abriendo el Microsoft Office host de aplicación o ejecutando *VSTOInstaller.exe*.

 La primera comprobación de seguridad tan solo se aplica a las soluciones de nivel de documento. El documento de una solución de nivel de documento debe estar en una ubicación de confianza. Si el documento se encuentra en un recurso compartido de archivos de red remoto o tiene una extensión de nombre de archivo *. doc* o *. docm* , la ubicación del documento debe agregarse a la lista de ubicaciones de confianza. Para obtener más información, vea [conceder confianza a los documentos](../vsto/granting-trust-to-documents.md).

 ![Seguridad de VSTO: Instalar desde Microsoft Office](../vsto/media/host-install.png "Seguridad de VSTO: Instalar desde Microsoft Office")

 El siguiente conjunto de comprobaciones de seguridad son de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y ClickOnce. Para poder pasar estas comprobaciones, las soluciones de Office deben solicitar permisos FullTrust, estar firmadas con un certificado que no aparezca en la lista de editores que no son de confianza, y hallarse en una ubicación que no se encuentre en la zona restringida de Internet Explorer. Si el certificado está en la lista de editores de confianza, la solución se instala de inmediato. En caso contrario, si no produjo error en ninguna de las comprobaciones, la solución avanza hasta el conjunto final de las comprobaciones.

 ![Seguridad de VSTO para instalar soluciones](../vsto/media/installing.png "Seguridad de VSTO para instalar soluciones")

 Si [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] se permite el aviso de confianza y aún no se ha concedido confianza a la solución, el tiempo de ejecución permitirá que el usuario final realice la decisión de confianza. Si el usuario concede confianza a la solución, se agrega una entrada a la lista de inclusión del usuario. Todas las soluciones de la lista de inclusión del usuario tienen plena confianza y pueden instalarse y ejecutarse.

 A partir de Visual Studio 2010, la lista de inclusión se omite si la solución de Office se instala mediante Windows Installer (MSI) en el directorio Archivos de programa. Para obtener más información, consulte [confiar en las soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Seguridad de VSTO: usar el programa de instalación para realizar la instalación](../vsto/media/setup-vstoinstaller.png "Seguridad de VSTO: usar el programa de instalación para realizar la instalación")

## <a name="see-also"></a>Consulte también

- [Conceder confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)
- [Conceder confianza a los documentos](../vsto/granting-trust-to-documents.md)
- [Confiar en soluciones de Office mediante listas de inclusión](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Cómo: configurar la seguridad de la lista de inclusión](../vsto/how-to-configure-inclusion-list-security.md)
- [Cómo: firmar soluciones de Office](../vsto/how-to-sign-office-solutions.md)
- [Solucionar problemas de seguridad de soluciones de Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Referencia a ClickOnce](../deployment/clickonce-reference.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
