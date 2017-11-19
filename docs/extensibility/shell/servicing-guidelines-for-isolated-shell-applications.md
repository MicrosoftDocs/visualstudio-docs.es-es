---
title: Mantenimiento de instrucciones de aislamiento de las aplicaciones de Shell | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f99631db1709a17aaf9809669bbeb2f69b10e2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Directrices de servicio para las aplicaciones de Shell aislado
Cuando se distribuye una aplicación de shell aislado de Visual Studio, debe ser capaz de proporcionar actualizaciones de software para la aplicación después de instalarlo. Para ello, debe instalar la aplicación mediante un archivo de Microsoft Installer (MSI). Este tipo de instalación permite que las actualizaciones de software proporcionadas por Microsoft para Web, se pueden redistribuir descargarán y utilizado por los clientes sin la intervención del personalizado.  
  
## <a name="servicing-requirements"></a>Requisitos de mantenimiento  
 Puede asegurarse de que la instalación de shell aislado puede permitir que las actualizaciones, asegúrese de que el programa de instalación cumple los tres criterios siguientes.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuir mediante el uso de un archivo MSI  
 Debe utilizar un archivo MSI para redistribuir la aplicación, porque un archivo MSI conserva la identidad del producto y asegura de la aplicación tiene una ubicación física en el equipo cliente. Los módulos de combinación (archivos .msm) no proporcionan garantías de este tipo y no deben usarse.  
  
### <a name="accounting-for-custom-actions"></a>Teniendo en cuenta las acciones personalizadas  
 Las acciones personalizadas son directivas de instalación no estándar en un programa de instalación. Acciones personalizadas cambian como ubicaciones de archivos, configuración del registro, configuración de usuario u otros elementos de la instalación. Acciones personalizadas pueden manipular los datos en tiempo de instalación.  
  
 Si utilizas acciones personalizadas en un programa de instalación, debe asegurarse de que todas las acciones personalizadas durante la instalación deben tener una acción personalizada correspondiente para deshacer la acción cuando el usuario desinstala la aplicación. Si el programa de instalación produce un error para proporcionar correspondiente desinstala la acción personalizada, quitar la aplicación lo dejará parcialmente instalado.  
  
-   Una acción personalizada que se basa en una versión específica de los valores hash o el archivo no se podrá cambien estas versiones de las actualizaciones de software o valores hash. En este caso la acción personalizada debe actualizar manualmente estos valores. Si las versiones de un archivo o hash los valores se comparten entre las versiones de producto, se produce un problema adicional. Evite esta dependencia siempre que sea posible.  
  
### <a name="accounting-for-shared-files"></a>Teniendo en cuenta los archivos compartidos  
 Archivos compartidos tienen los mismos nombres y se instalan en la misma ubicación de varios productos. Estos productos pueden ser diferente de la versión, unidad de mantener existencias (SKU) o ambos, y los productos pueden coexistir en un equipo determinado. Sin embargo, los archivos compartidos crean problemas de mantenimiento por varias razones:  
  
-   Actualizar los archivos compartidos puede dar lugar a problemas de compatibilidad de aplicaciones porque una actualización de una aplicación puede cambiar la versión del archivo utilizado por una segunda aplicación que no se ha actualizado. Instaladores para los productos que comparten las referencias de recuento de archivos a los archivos compartidos. Por lo tanto, al desinstalar un producto no afecta a los archivos compartidos más allá de disminuir el recuento de instancias instaladas.  
  
-   El instalador de ingeniería de corrección rápida (QFE) revierte las versiones de archivos a las versiones de los productos que da servicio el instalador QFE. Este proceso potencialmente interrumpe una aplicación que había entregado a un archivo compartido actualizado.