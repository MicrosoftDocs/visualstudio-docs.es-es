---
title: Solucionar problemas de seguridad de soluciones de Office
description: Conozca algunas sugerencias para solucionar problemas comunes que pueden surgir al trabajar con la protección de soluciones de Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04b68a8207dad1edf83462a8284a69c73c668006
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969209"
---
# <a name="troubleshoot-office-solution-security"></a>Solucionar problemas de seguridad de soluciones de Office
  Este tema contiene sugerencias para solucionar problemas comunes que pueden surgir al trabajar con la protección de soluciones de Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Las soluciones de confianza no se pueden instalar desde sitios restringidos
 Los usuarios no pueden instalar una solución desde una ubicación Web si el sitio web se muestra en la zona Sitios restringidos de Internet Explorer. Esto es así incluso si la solución está firmada con un certificado de confianza.

 La dirección URL del manifiesto de implementación se puede clasificar en una de las cinco zonas siguientes:

- Mi PC

- Internet

- Intranet local

- Sitios de confianza

- Sitios restringidos

  Si la ubicación del manifiesto de implementación se ha asignado a la zona de sitios restringidos, no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instala la solución. Si la ubicación es conocida y se puede confiar en ella, el usuario puede quitar la ubicación de la zona de sitios restringidos e instalar la solución. Para obtener información acerca de cómo administrar zonas, vea [configurar editores de confianza de ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>No se pueden instalar soluciones desde recursos compartidos de archivos de red o ubicaciones Web cuando la configuración de seguridad mejorada de Internet Explorer o Internet Explorer 7 está instalado
 La configuración de seguridad mejorada (IEESC) de Internet Explorer en Windows Server 2003 y versiones posteriores, e Internet Explorer 7 y versiones posteriores, restringe significativamente la capacidad de los usuarios de explorar Internet. Cuando los usuarios intentan instalar soluciones de Office desde un recurso compartido de archivos de red o desde una ubicación Web, pueden recibir el siguiente mensaje de error: "la funcionalidad personalizada en esta aplicación no funcionará porque el certificado usado para firmar el manifiesto de implementación para *solutionname* no es de confianza. Póngase en contacto con el administrador para obtener más ayuda ".

 Con IEESC e Internet Explorer 7 y versiones posteriores, si la dirección URL del manifiesto de implementación se clasifica en la zona de Internet, el manifiesto debe tener un certificado de un editor de confianza o no se puede instalar la solución. Sin IEESC, el comportamiento predeterminado es solicitar al usuario final que tome una decisión de confianza.

 Para administrar el efecto de IEESC e Internet Explorer 7 y versiones posteriores, identifique los sitios web y las rutas de acceso UNC (Convención de nomenclatura universal) en las que confía y agréguelos a una de las zonas de seguridad de confianza (Intranet local o sitios de confianza). Para obtener información sobre cómo administrar las zonas, vea [configurar editores de confianza de ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Solucionar problemas de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
