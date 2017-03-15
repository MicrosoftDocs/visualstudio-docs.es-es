---
title: "El mantenimiento de las directrices de aplicaciones de Shell aislado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio Shell el modo integrado, capacidad de servicio"
  - "Modo integrado de shell [Visual Studio], capacidad de servicio"
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# El mantenimiento de las directrices de aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se distribuye una aplicación de shell aislado de Visual Studio, debe ser capaz de proporcionar actualizaciones de software de la aplicación después de instalarlo. Para ello, debe instalar la aplicación mediante un archivo de Microsoft Installer \(MSI\). Este tipo de instalación permite que las actualizaciones de software de Microsoft para redistribuir mediante Web descargarán y utilizado por los clientes sin intervención personalizado.  
  
## Requisitos de mantenimiento  
 Puede asegurarse de que la instalación de shell aislado puede permitir actualizaciones asegurándose de que el programa de instalación cumple los tres criterios siguientes.  
  
### Redistribuir mediante el uso de un archivo MSI  
 Debe utilizar un archivo MSI para redistribuir la aplicación, ya que conserva la identidad de producto MSI y asegura de la aplicación tiene una ubicación física en el equipo cliente. Los módulos de combinación \(archivos .msm\) no ofrecen dichas garantías y no deben usarse.  
  
### Teniendo en cuenta las acciones personalizadas  
 Las acciones personalizadas son las directivas de instalación no estándar en un programa de instalación. Acciones personalizadas cambian parámetros como ubicaciones de archivos, configuración del registro, configuración de usuario u otros elementos de la instalación. Acciones personalizadas pueden manipular los datos en tiempo de instalación.  
  
 Al usar acciones personalizadas en un programa de instalación, debe asegurarse de que todas las acciones personalizadas durante la instalación deben tener una acción personalizada correspondiente para deshacer la acción cuando el usuario desinstala la aplicación. Si el programa de instalación produce un error para proporcionar correspondiente desinstala acción personalizada, la eliminación de la aplicación lo dejará parcialmente instalado.  
  
-   Una acción personalizada que se basa en una versión específica de un archivo o hash de los valores no se podrá cambian estas versiones de las actualizaciones de software o valores hash. En este caso la acción personalizada debe actualizar manualmente estos valores. Si las versiones de un archivo o hash de los valores se comparten entre las versiones de producto, se produce un problema adicional. Evite esta dependencia siempre que sea posible.  
  
### Teniendo en cuenta los archivos compartidos  
 Archivos compartidos con los mismos nombres y se instalan en la misma ubicación de varios productos. Estos productos pueden diferir en versión o unidad de mantener existencias \(SKU\) y los productos pueden coexistir en un equipo determinado. Sin embargo, los archivos compartidos crean problemas de mantenimiento por varias razones:  
  
-   Actualizar los archivos compartidos puede provocar problemas de compatibilidad de aplicaciones, dado que una actualización de una aplicación puede cambiar la versión de un archivo de una segunda aplicación que no se ha actualizado. Los instaladores para los productos que comparten los archivos de recuento de referencias a los archivos compartidos. Por lo tanto, la desinstalación de un producto no afecta a los archivos compartidos más allá de disminuir el recuento de instancias instaladas.  
  
-   El instalador de ingeniería de corrección rápida \(QFE\) revierte las versiones de archivos a las versiones de los productos que atiende el instalador QFE. Este proceso interrumpe potencialmente una aplicación que se había entregado a un archivo compartido actualizado.