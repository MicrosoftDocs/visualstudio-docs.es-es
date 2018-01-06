---
title: "Solucionar problemas de seguridad de la solución de Office | Documentos de Microsoft"
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
helpviewer_keywords: security [Office development in Visual Studio], troubleshooting
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3cc5656877f3e6c1ee578a53345e2482c2103223
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-office-solution-security"></a>Solucionar problemas de seguridad de soluciones de Office
  Este tema contiene sugerencias para resolver problemas comunes que pueden surgir al trabajar con la protección de las soluciones de Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>No se puede instalar soluciones de sitios restringidos de confianza  
 Los usuarios no pueden instalar una solución desde una ubicación web si el sitio web se muestra en la zona de sitios restringidos de Internet Explorer. Esto es cierto incluso si la solución está firmada con un certificado de confianza.  
  
 La dirección URL del manifiesto de implementación se puede clasificar en uno de los cinco zonas:  
  
-   Mi equipo  
  
-   Internet  
  
-   Intranet local  
  
-   Sitios de confianza  
  
-   Sitios restringidos  
  
 Si la ubicación del manifiesto de implementación se ha asignado a la zona de sitios restringidos, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] no instala la solución. Si la ubicación se conoce y puede ser de confianza, el usuario puede quitar la ubicación de la zona de sitios restringidos e instalar la solución. Para obtener información acerca de cómo administrar zonas, vea [Configurar editores de confianza de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>No se puede instalar soluciones desde recursos compartidos de archivos de red o ubicaciones Web cuando la configuración de seguridad mejorada de Internet Explorer o Internet Explorer 7 está instalado  
 Internet Explorer Enhanced seguridad configuración (IEESC) en Windows Server 2003 y versiones posteriores e Internet Explorer 7 y versiones posterior, restringe la capacidad de los usuarios a navegar por Internet. Cuando los usuarios intentan instalar soluciones de Office desde una ubicación de web o recurso compartido de archivos de red, puede que aparezca el siguiente mensaje de error: "funcionalidad personalizada de esta aplicación no funcionará porque el certificado utilizado para firmar el manifiesto de implementación para *SolutionName* no es de confianza. Póngase en contacto con el administrador para obtener más ayuda."  
  
 Con IEESC e Internet Explorer 7 y versiones posterior, si la dirección URL del manifiesto de implementación se clasifica por categorías en la zona de Internet, el manifiesto debe tener un certificado de un publicador de confianza o no se puede instalar la solución. Sin IEESC, el comportamiento predeterminado es preguntar al usuario final para tomar una decisión de confianza.  
  
 Para administrar el efecto de IEESC e Internet Explorer 7 y versiones posteriores, identificar sitios web y rutas de nomenclatura universal (UNC) convención confía y agregarlos a una de las zonas de seguridad de confianza (intranet Local o sitios de confianza). Para obtener información acerca de cómo administrar zonas, vea [Configurar editores de confianza de ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## <a name="see-also"></a>Vea también  
 [Protección de soluciones de Office](../vsto/securing-office-solutions.md)  
  
  