---
title: Compilación y depuración de soluciones de SharePoint | Microsoft Docs
description: Obtenga información sobre cómo compilar y depurar soluciones de SharePoint, y descubra la diferencia que hay con la compilación y la depuración de otros tipos de proyectos de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f6801f6b60d2ef522385ecdf290d0a1913bd6df2
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850239"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Build and debug SharePoint solutions (Compilar y depurar las soluciones de SharePoint)
  En general, la compilación y depuración de soluciones de SharePoint es la misma que la de otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Los temas de esta sección explican las diferencias que existen entre ellos.

## <a name="project-output-for-sharepoint-solutions"></a>Resultados del proyecto para soluciones de SharePoint
 La compilación de soluciones de SharePoint crea ensamblados y un archivo de paquete de solución ( *.wsp*). En la tabla siguiente se muestran las ubicaciones de estos archivos durante una compilación.

|Elemento de compilación|Carpeta de salida|
|----------------|-------------------|
|Ensamblado, base de datos de programa ( *.pdb*) y archivos *.wsp*.|*\<ProjectName>\bin\debug* o *\<ProjectName>\bin\release*|
|Archivos de elemento de proyecto de SharePoint.|*\<ProjectName>\pkg\debug* o *\<ProjectName>\pkg\release*|
|Compilación de archivos intermedios.|*\<ProjectName>\obj\debug* o *\<ProjectName>\obj\release*|
|Empaquetado de archivos intermedios.|*\<ProjectName>\pkgobj\debug* o *\<ProjectName>\pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Compilación de soluciones de SharePoint
 Para compilar soluciones de SharePoint, el equipo de desarrollo debe tener instalada la versión correcta de SharePoint Server. De lo contrario, la compilación de soluciones de SharePoint es la misma que la de otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, vea [Cómo: para compilar soluciones de SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Depuración y prueba de soluciones de SharePoint
 Antes de la depuración, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia el paquete *.wsp* en el servidor de SharePoint, activa las características con ámbito de sitio y web y, en algunos casos, inicia el proyecto. En otros casos, es posible que tenga que abrir el proyecto manualmente. Para obtener más información, vea [Solución de problemas de las soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) y [Depuración de soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Depuración y comprobación de las soluciones de SharePoint mediante características de Azure DevOps Services
 Las características de Azure DevOps Services como las pruebas unitarias e IntelliTrace permiten identificar con mayor precisión los problemas de las soluciones de SharePoint. La generación de perfiles permite localizar e identificar áreas problemáticas de rendimiento en las soluciones de SharePoint. Para obtener más información, vea [Comprobación y depuración de código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) y [Generación de perfiles de rendimiento de aplicaciones de SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Seguridad durante el proceso de compilación
 Para empaquetar o implementar soluciones de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debe tener permiso para copiar archivos en el servidor de SharePoint. Debe ejecutar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como un proceso con privilegios elevados, y la cuenta de usuario debe ser un administrador de colecciones de sitios en el servidor de SharePoint. Además, debe especificar si el proyecto es una solución de espacio aislado o de granja. Para obtener más información, vea [Diferencias entre soluciones de espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Uso del comando Clean
 Cuando una solución de SharePoint se instala en un servidor de SharePoint para la depuración, el comando **Clean** no la desinstala. En su lugar, debe desactivar las características a través de la configuración de SharePoint.

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Examen de las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Empaquetado e implementación de soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
