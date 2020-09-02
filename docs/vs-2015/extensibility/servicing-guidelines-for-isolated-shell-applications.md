---
title: Instrucciones de servicio para las aplicaciones de Shell aislado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159273"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Directrices de servicio para aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se distribuye una aplicación de Shell aislado de Visual Studio, debe ser capaz de proporcionar actualizaciones de software para la aplicación después de instalarla. Para ello, debe instalar la aplicación mediante un archivo de Microsoft Installer (MSI). Este tipo de instalación permite que las actualizaciones de software proporcionadas por Microsoft se redistribuyan mediante descarga web y las consuman los clientes sin intervención personalizada.  
  
## <a name="servicing-requirements"></a>Requisitos de mantenimiento  
 Puede asegurarse de que la instalación de Shell aislado puede permitir actualizaciones asegurándose de que el programa de instalación cumple los tres criterios siguientes.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuir mediante una MSI  
 Debe usar una MSI para redistribuir la aplicación, ya que una MSI conserva la identidad del producto y se asegura de que la aplicación tenga una ubicación física en el equipo cliente. Los módulos de combinación (archivos. MSM) no proporcionan tales garantías y no deben usarse.  
  
### <a name="accounting-for-custom-actions"></a>Contabilidad de acciones personalizadas  
 Las acciones personalizadas son directivas de instalación no estándar en un programa instalador. Las acciones personalizadas cambian parámetros como las ubicaciones de archivo, la configuración del registro, la configuración de usuario u otros elementos de instalación. Las acciones personalizadas podrían manipular los datos en el momento de la instalación.  
  
 Al usar acciones personalizadas en un programa de instalación, debe asegurarse de que todas las acciones personalizadas en tiempo de instalación deben tener una acción personalizada correspondiente para deshacer la acción cuando el usuario desinstale la aplicación. Si el programa de instalación no puede proporcionar la acción personalizada de desinstalación correspondiente, al quitar la aplicación se dejará parcialmente instalada.  
  
- Una acción personalizada que se basa en una versión específica de un archivo o valores hash producirá un error cuando las actualizaciones de software cambien estas versiones o valores hash. En este caso, la acción personalizada debe actualizar manualmente estos valores. Se produce un problema adicional si se comparten versiones de un archivo o valores hash entre versiones del producto. Evite esta dependencia siempre que sea posible.  
  
### <a name="accounting-for-shared-files"></a>Cuentas de archivos compartidos  
 Los archivos compartidos tienen los mismos nombres y se instalan en la misma ubicación en varios productos. Estos productos pueden diferir en la versión, la referencia de almacén (SKU) o ambos, y los productos pueden coexistir en un equipo determinado. Sin embargo, los archivos compartidos crean problemas de servicio por varias razones:  
  
- La actualización de los archivos compartidos puede causar problemas de compatibilidad de aplicaciones porque una actualización de una aplicación puede cambiar la versión de un archivo utilizado por una segunda aplicación que no se ha actualizado. Los instaladores de los productos que comparten referencias de recuento de archivos a los archivos compartidos. Por lo tanto, la desinstalación de un producto no afecta a los archivos compartidos más allá de reducir el número de instancias instaladas.  
  
- El instalador de la ingeniería de corrección rápida (QFE) revierte las versiones de los archivos a las versiones de los productos que el instalador QFE ha dado servicio. Este proceso puede interrumpir una aplicación que ha entregado un archivo compartido actualizado.
