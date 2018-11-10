---
title: Cómo actualizar proyectos a la versión actual de las herramientas de Azure | Microsoft Docs
description: Obtenga información sobre cómo actualizar un proyecto de Azure en Visual Studio a la versión actual de las herramientas de Azure
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c5fb70f2dd09338dd2e2f6b01cb60bf2be0cdbdd
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002906"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Actualización de proyectos a la versión actual de Azure Tools para Visual Studio
## <a name="overview"></a>Información general
Después de instalar la versión actual de las herramientas de Azure (o una versión anterior que sea posterior a la 1.6), todos los proyectos que se crearon con una Azure Tools versión 1.6 (noviembre de 2011) se actualizarán automáticamente en cuanto se abran. Si creó proyectos con la versión 1.6 de (noviembre de 2011) de las herramientas y sigue teniendo esa versión instalada, puede abrir estos proyectos en la versión anterior y decidir más tarde si desea actualizarlos.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>¿Cómo se cambia el proyecto al actualizarlo
Si un proyecto se actualiza automáticamente o especifique que desea actualizarlo, el proyecto se modifica para trabajar con las versiones actuales de ciertos ensamblados y también se modifican algunas propiedades como se describe en esta sección. Si el proyecto requiere otros cambios para que sea compatible con la versión más reciente de las herramientas, debe realizar los cambios manualmente.

* El archivo web.config para roles web y el archivo app.config para roles de trabajo se actualizan para hacer referencia a la versión más reciente de Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitoirTraceListener.dll.
* Los ensamblados Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll y Microsoft.WindowsAzure.ServiceRuntime.dll se actualizan a las nuevas versiones.
* Perfiles de publicación que se almacenaron en el archivo de proyecto de Azure (.ccproj) se mueven a un archivo independiente, con la extensión .azurePubXml, en el **publicar** subdirectorio.
* Algunas propiedades del perfil de publicación se actualizan para admitir características nuevas y modificadas. **AllowUpgrade** se sustituye por **DeploymentReplacementMethod** ya que puede actualizar un servicio en la nube implementado simultáneamente o de forma incremental.
* La propiedad **UseIISExpressByDefault** se agrega y se establece en false para que el servidor web que se usa para la depuración no cambie automáticamente de Internet Information Services (IIS) para IIS Express. IIS Express es el servidor web predeterminado para los proyectos creados con las versiones más recientes de las herramientas.
* Si el almacenamiento en caché de Azure se hospeda en uno o varios de los roles del proyecto, algunas propiedades en la configuración del servicio (archivo .cscfg) y la definición de servicio (archivo .csdef) se cambian cuando se actualiza un proyecto. Si el proyecto usa el paquete NuGet de almacenamiento en caché de Azure, el proyecto se actualiza a la versión más reciente del paquete. Debe abrir el archivo web.config y compruebe que la configuración del cliente se mantuvo correctamente durante el proceso de actualización. Si agrega las referencias a ensamblados de cliente de almacenamiento en caché de Azure sin usar el paquete de NuGet, estos ensamblados no se actualizarán; debe actualizar manualmente las referencias a las nuevas versiones.

> [!IMPORTANT]
> Para F# proyectos, debe actualizar manualmente las referencias a los ensamblados de Azure para que hagan referencia a las versiones más recientes de dichos ensamblados.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Cómo actualizar un proyecto de Azure a la versión actual
1. Instalar la versión actual de las herramientas de Azure en la instalación de Visual Studio que desea usar para el proyecto actualizado y, a continuación, abra el proyecto que desea actualizar. Si el proyecto se creó con un Azure Tools versión 1.6 (noviembre de 2011), el proyecto se actualiza automáticamente a la versión actual. Si el proyecto se creó con la de noviembre de 2011 de versión y esa versión todavía está instalada, el proyecto se abre en esa versión.
2. En el Explorador de soluciones, abra el menú contextual del nodo de proyecto, elija **propiedades**y, a continuación, elija el **aplicación** ficha del cuadro de diálogo que aparece.
   
    El **aplicación** pestaña muestra la versión de herramientas que está asociado con el proyecto. Si aparece la versión actual de las herramientas de Azure, el proyecto ya se ha actualizado. Si ha instalado una versión más reciente de las herramientas que se muestra en la ficha, un **actualizar** aparece el botón.
3. Elija la **actualizar** botón para actualizar un proyecto a la versión actual de las herramientas.
4. Compile el proyecto y, a continuación, solucione los errores derivados de los cambios de API. Para obtener información acerca de cómo modificar el código para la nueva versión, consulte la documentación de la API específica.

