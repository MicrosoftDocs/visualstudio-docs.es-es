---
title: "Instalaci&#243;n de VSPackages con Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalación [Visual Studio SDK] con Windows Installer"
  - "VSPackages, implementar"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# Instalaci&#243;n de VSPackages con Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Integración de VSPackage en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] requiere más que copiar los archivos en el equipo de un usuario.  El instalador de VSPackage debe instalar el Paquete y sus archivos dependientes, y registro e integrarlos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  El Paquete puede aprovechar características de integración como mostrar un icono en la pantalla de presentación de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y el cuadro de diálogo Acerca de.  
  
 Los archivos de Microsoft Windows Installer son la forma recomendada de distribuir el VSPackages.  Los paquetes de Windows Installer fáciles de usar se pueden ejecutar en cualquier sistema operativo Windows compatible con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea [Windows Installer](http://msdn.microsoft.com/es-es/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## En esta sección  
 [Fundamentos de Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Proporciona información general de Windows Installer.  
  
 [Escenarios de instalación de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Describe maneras diferentes que puede admitir en paralelo las instalaciones de VSPackages y de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Creación de un paquete de Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Proporciona información general de los pasos comunes que los instaladores siguen correctamente a la instalación y que integran VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Detectar los requisitos del sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Describe cómo un instalador puede detectar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y sus componentes y configuración de cancelación si los requisitos de VSPackage no se cumplen.  
  
 [Administración de componentes](../../extensibility/internals/component-management.md)  
 Describe cómo desarrollar un instalador que mantiene la integridad de las versiones anteriores del producto.  
  
 [Elija el directorio de instalación de un paquete VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Resume las opciones para buscar VSPackages.  
  
 [Registro de VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Explica cómo VSPackages se registra en tiempo de instalación y por qué el registro automático es una idea incorrecta.  
  
 [Tipos de proyecto de implementación](../../extensibility/internals/deploying-project-types.md)  
 Explica cómo utilizar el nuevo agregador del tipo de proyecto para los tipos de proyecto de código administrado.  
  
 [Cómo: generar la información de registro de un instalador](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Explica cómo utilizar RegPkg.exe para generar un registro manifiesto para un VSPackage administrado.  
  
 [Comandos que se deben ejecutar después de la instalación](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Explica cómo ejecutar comandos de la instalación de integrar VSPackages en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Desinstalación de un paquete VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Describe los pasos que debe ejecutar el instalador cuando los usuarios por el paquete VSPackage.  
  
## Secciones relacionadas  
 [Instalar VSPackages](../../misc/installing-vspackages.md)  
 Explica cómo compilar e instalar VSPackages y cómo admitir usuarios que ejecutan varias versiones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al mismo tiempo.