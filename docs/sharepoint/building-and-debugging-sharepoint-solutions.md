---
title: Compilar y depurar soluciones de SharePoint | Microsoft Docs
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
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016359"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Build and debug SharePoint solutions (Compilar y depurar las soluciones de SharePoint)
  En general, la compilación y depuración de soluciones de SharePoint es lo mismo que generar y depurar otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Los temas de esta sección explican las diferencias que existen entre ellos.

## <a name="project-output-for-sharepoint-solutions"></a>Resultados del proyecto para soluciones de SharePoint
 Al crear soluciones de SharePoint, se crean ensamblados y un archivo de paquete de solución (*. wsp*). En la tabla siguiente se muestran las ubicaciones de estos archivos durante una compilación.

|Elemento de compilación|Carpeta de salida|
|----------------|-------------------|
|Archivos de ensamblado, base de datos de programa (*. pdb*) y *. wsp* .|* \<ProjectName> \bin\debug* o * \<ProjectName> \bin\release*|
|Archivos de elemento de proyecto de SharePoint.|* \<ProjectName> \pkg\debug* o * \<ProjectName> \pkg\release*|
|Compilar archivos intermedios.|* \<ProjectName> \obj\debug* o * \<ProjectName> \obj\release*|
|Empaquetar archivos intermedios.|* \<ProjectName> \pkgobj\debug* o * \<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Compilar soluciones de SharePoint
 Para compilar soluciones de SharePoint, el equipo de desarrollo debe tener instalada la versión correcta de SharePoint Server. De lo contrario, la creación de soluciones de SharePoint es igual que generar otros tipos de proyectos en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para obtener más información, vea [Cómo: compilar soluciones de SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Depurar y probar soluciones de SharePoint
 Antes de la depuración, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia el paquete *. wsp* en el servidor de SharePoint, activa las características de ámbito Web y de sitio, y en algunos casos inicia el proyecto. En otros casos, puede que tenga que abrir el proyecto manualmente. Para obtener más información, vea [solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) y [depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Depurar y comprobar las soluciones de SharePoint mediante el uso de Azure DevOps Services características
 Azure DevOps Services características como las pruebas unitarias y IntelliTrace permiten identificar con mayor precisión los problemas de las soluciones de SharePoint. La generación de perfiles permite localizar e identificar áreas problemáticas de rendimiento en las soluciones de SharePoint. Para obtener más información, vea [comprobar y depurar código de SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) y [generar perfiles del rendimiento de las aplicaciones de SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Seguridad durante el proceso de compilación
 Para empaquetar o implementar soluciones de SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debe tener permiso para copiar archivos en el servidor de SharePoint. Debe ejecutar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como un proceso con privilegios elevados y su cuenta de usuario debe ser un administrador de colecciones de sitios en el servidor de SharePoint. Además, debe especificar si el proyecto es una solución en espacio aislado o una solución de granja. Para obtener más información, vea [diferencias entre las soluciones en espacio aislado y las soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Uso del comando Clean
 Cuando se instala una solución de SharePoint en un servidor de SharePoint para la depuración, el comando **limpiar** no desinstala la solución. En su lugar, debe desactivar las características a través de la configuración de SharePoint.

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Examinar las conexiones de SharePoint mediante Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
