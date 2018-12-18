---
title: Directrices para de servicio de aplicaciones de Shell aisladas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a795e5dc71183550e660f8ce7d67f1a41bddbcf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726780"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Directrices de servicio para aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se distribuye una aplicación de shell aislado de Visual Studio, debe ser capaz de proporcionar actualizaciones de software para su aplicación después de instalarlo. Para ello, debe instalar la aplicación mediante un archivo Microsoft Installer (MSI). Este tipo de instalación permite que las actualizaciones de software proporcionadas por Microsoft para redistribuir mediante Web descargarán y consuman por los clientes sin intervención personalizado.  
  
## <a name="servicing-requirements"></a>Los requisitos de mantenimiento  
 Puede asegurarse de que la instalación de shell aislado puede permitir que las actualizaciones asegurándose de que el programa de instalación cumple los tres criterios siguientes.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuir mediante un archivo MSI  
 Debe usar un archivo MSI para redistribuir la aplicación, ya que conserva la identidad de producto MSI y asegura de la aplicación tiene una ubicación física en el equipo cliente. Módulos de combinación (archivos .msm) no proporcionan garantías de este tipo y no deben usarse.  
  
### <a name="accounting-for-custom-actions"></a>Teniendo en cuenta las acciones personalizadas  
 Las acciones personalizadas son las directivas de instalación no estándar en un programa de instalación. Acciones personalizadas cambian los parámetros como ubicaciones de archivos, configuración del registro, configuración de usuario ni otros elementos de la instalación. Acciones personalizadas pueden manipular los datos en tiempo de instalación.  
  
 Al usar las acciones personalizadas en un programa de instalación, debe asegurarse de que todas las acciones personalizadas durante la instalación deben tener una acción personalizada correspondiente para deshacer la acción cuando el usuario desinstala la aplicación. Si el programa de instalación produce un error para proporcionar la correspondiente acción personalizada desinstala, quitar la aplicación lo dejará parcialmente instalado.  
  
-   Una acción personalizada que se basa en una versión específica de un archivo o hash de valores se producirá un error al cambian estas versiones de las actualizaciones de software o valores hash. En este caso la acción personalizada debe actualizar manualmente estos valores. Se produce un problema adicional si las versiones de un archivo o hash de valores que se comparten entre las versiones de producto. Evite esta dependencia siempre que sea posible.  
  
### <a name="accounting-for-shared-files"></a>Teniendo en cuenta los archivos compartidos  
 Archivos compartidos con los mismos nombres y se instalan en la misma ubicación de varios productos. Estos productos pueden diferir en versión de Stock mantener unidad (SKU) o ambos, y los productos pueden coexistir en un equipo determinado. Sin embargo, los archivos compartidos crean problemas de mantenimiento por varias razones:  
  
-   Actualizar los archivos compartidos puede provocar problemas de compatibilidad de aplicaciones, dado que una actualización de una aplicación puede cambiar la versión de un archivo utilizado por una segunda aplicación que no se ha actualizado. Los instaladores para los productos que comparten los archivos de recuento de referencias a los archivos compartidos. Por lo tanto, la desinstalación de un producto no afecta a los archivos compartidos más allá de disminuir el recuento de instancias instaladas.  
  
-   El instalador de ingeniería de corrección rápida (QFE) revierte las versiones de archivos a las versiones de los productos que atienden el instalador QFE. Este proceso interrumpe potencialmente una aplicación que había entregado a un archivo compartido actualizado.

